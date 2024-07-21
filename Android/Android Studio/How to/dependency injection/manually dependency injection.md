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

Then 
## Ref
See [manually dependency injection in Android Studio](https://developer.android.com/training/dependency-injection/manual)
