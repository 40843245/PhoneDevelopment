# manually dependency injection in Android Studio
## Way 1:
### Example
Consider the following tree.

![image](https://github.com/user-attachments/assets/fc82f4f1-c9ae-4237-9c73-3030137a456e)

In the above example, one can know these facts.

+ entry point : `LoginActivity` that is an entry point the login flow and the user interacts with the activity.
+ Thus, `LoginActivity` needs to create its all dependencies (here is all descendent of `LoginActivity`).
+ `LoginActivity` descendents:

  - `LoginViewModel`
    - `UserRepository`
      - `UserLocalDataSource`
      - `UserRemoteDataSource`
        - `Retorfit` 

+ Thus, the `Repository` and `DataSource` classes of the flow will look like this:

```
  class UserRepository(
    private val localDataSource: UserLocalDataSource,
    private val remoteDataSource: UserRemoteDataSource
) { ... }

class UserLocalDataSource { ... }
class UserRemoteDataSource(
    private val loginService: LoginRetrofitService
) { ... }
```

+ While `LoginActivity` will Look like this:

```
class LoginActivity: Activity() {

    private lateinit var loginViewModel: LoginViewModel

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // In order to satisfy the dependencies of LoginViewModel, you have to also
        // satisfy the dependencies of all of its dependencies recursively.
        // First, create retrofit which is the dependency of UserRemoteDataSource
        val retrofit = Retrofit.Builder()
            .baseUrl("https://example.com")
            .build()
            .create(LoginService::class.java)

        // Then, satisfy the dependencies of UserRepository
        val remoteDataSource = UserRemoteDataSource(retrofit)
        val localDataSource = UserLocalDataSource()

        // Now you can create an instance of UserRepository that LoginViewModel needs
        val userRepository = UserRepository(localDataSource, remoteDataSource)

        // Lastly, create an instance of LoginViewModel with userRepository
        loginViewModel = LoginViewModel(userRepository)
    }
}
```

### issue of Way 1:
Continue the above example. With this approach, there are issues.

+ boilerplate code : There's a lot of boilerplate code.
+ dependencies have to be declared in order : Since dependencies have to be declared in order, You have to instantiate UserRepository before LoginViewModel in order to create it.
+ difficult to reuse : It's difficult to reuse objects. Voilating the feature of dependency injection (one feature is that easy to maintain (including reuse, extend etc) for more details, see [my notes at Github - dependency injection](https://github.com/40843245/computer-science/blob/main/term/link%20of%20dependency%20injection.md)

## Way 2: Use the container

To solve the issue with approach that used in Way 1, one can create a class that behaves as a container.

### Example 
Continue the above example, one can rewrite it as

```
// Container of objects shared across the whole app
class AppContainer {

    // Since you want to expose userRepository out of the container, you need to satisfy
    // its dependencies as you did before
    private val retrofit = Retrofit.Builder()
                            .baseUrl("https://example.com")
                            .build()
                            .create(LoginService::class.java)

    private val remoteDataSource = UserRemoteDataSource(retrofit)
    private val localDataSource = UserLocalDataSource()

    // userRepository is not private; it'll be exposed
    val userRepository = UserRepository(localDataSource, remoteDataSource)
}
```

To create a `LoginActivity` class, first create a class `MyApplication` that inherits `Application` and in the class simply instantiate the `AppContainer ` class.

```
// Custom Application class that needs to be specified
// in the AndroidManifest.xml file
class MyApplication : Application() {

    // Instance of AppContainer that will be used by all the Activities of the app
    val appContainer = AppContainer()
}
```

Lastly, write `LoginActivity` class as follows.

```
class LoginActivity: Activity() {

    private lateinit var loginViewModel: LoginViewModel

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // Gets userRepository from the instance of AppContainer in Application
        val appContainer = (application as MyApplication).appContainer
        loginViewModel = LoginViewModel(appContainer.userRepository)
    }
}
```

This approach is better than the previous one, but there are still some challenges to consider.

+ You have to manage AppContainer yourself, creating instances for all dependencies by hand.

+ There is still a lot of boilerplate code. You need to create factories or parameters by hand depending on whether you want to reuse an object or not.

On the other hand,

`AppContainer` gets complicated when you want to include more functionality in the project. When your app becomes larger and you start introducing different feature flows, there are even more problems that arise:

+ When you have different flows, you might want objects to just live in the scope of that flow. For example, when creating LoginUserData (that might consist of the username and password used only in the login flow) you don't want to persist data from an old login flow from a different user. You want a new instance for every new flow. You can achieve that by creating FlowContainer objects inside the AppContainer as demonstrated in the next code example.

+ Optimizing the application graph and flow containers can also be difficult. You need to remember to delete instances that you don't need, depending on the flow you're in.

## Way 3: Managing dependencies in application flows

Imagine you have a login flow that consists of one activity (`LoginActivity`) and multiple fragments (`LoginUsernameFragment` and `LoginPasswordFragment`). These views want to:

+ Access the same `LoginUserData` instance that needs to be shared until the login flow finishes.

+ Create a new instance of `LoginUserData` when the flow starts again.

You can achieve that with a login flow container. This container needs to be created when the login flow starts and removed from memory when the flow ends.

You want to be able to create multiple instances of LoginContainer in the app, so instead of making it a singleton, make it a class with the dependencies the login flow needs from the `AppContainer`. Code as follows.

```
class LoginContainer(val userRepository: UserRepository) {

    val loginData = LoginUserData()

    val loginViewModelFactory = LoginViewModelFactory(userRepository)
}

// AppContainer contains LoginContainer now
class AppContainer {
    ...
    val userRepository = UserRepository(localDataSource, remoteDataSource)

    // LoginContainer will be null when the user is NOT in the login flow
    var loginContainer: LoginContainer? = null
}
```

Once you have a container specific to a flow, you have to decide when to create and delete the container instance. Because your login flow is self-contained in an activity (`LoginActivity`), the activity is the one managing the lifecycle of that container. `LoginActivity` can create the instance in `onCreate()` method and delete it in `onDestroy()` method as following code.

```
class LoginActivity: Activity() {

    private lateinit var loginViewModel: LoginViewModel
    private lateinit var loginData: LoginUserData
    private lateinit var appContainer: AppContainer


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        appContainer = (application as MyApplication).appContainer

        // Login flow has started. Populate loginContainer in AppContainer
        appContainer.loginContainer = LoginContainer(appContainer.userRepository)

        loginViewModel = appContainer.loginContainer.loginViewModelFactory.create()
        loginData = appContainer.loginContainer.loginData
    }

    override fun onDestroy() {
        // Login flow is finishing
        // Removing the instance of loginContainer in the AppContainer
        appContainer.loginContainer = null
        super.onDestroy()
    }
}
```

Like `LoginActivity`, login fragments can access the `LoginContainer` from `AppContainer` and use the shared `LoginUserData` instance.

Because in this case you're dealing with view lifecycle logic, using [lifecycle observation(Android Studio official docs)](https://developer.android.com/topic/libraries/architecture/lifecycle) makes sense.

## [Conclusion](https://developer.android.com/training/dependency-injection/manual#conclusion)
Dependency injection is a good technique for creating scalable and testable Android apps. Use containers as a way to share instances of classes in different parts of your app and as a centralized place to create instances of classes using factories.

When your application gets larger, you will start seeing that you write a lot of boilerplate code (such as factories), which can be error-prone. You also have to manage the scope and lifecycle of the containers yourself, optimizing and discarding containers that are no longer needed in order to free up memory. Doing this incorrectly can lead to subtle bugs and memory leaks in your app.

In the [Dagger section](https://developer.android.com/training/dependency-injection/dagger-basics), you'll learn how you can use Dagger to automate this process and generate the same code you would have written by hand otherwise.

## Ref
See [manually dependency injection in Android Studio](https://developer.android.com/training/dependency-injection/manual)
