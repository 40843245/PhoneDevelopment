# manually dependency injection in Android Studio
## Example
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

The Repository and DataSource classes of the flow look like this:

## Ref
See [manually dependency injection in Android Studio](https://developer.android.com/training/dependency-injection/manual)
