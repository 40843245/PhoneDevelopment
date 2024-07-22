# [dependency injection in classes not supported by Hilt](https://developer.android.com/training/dependency-injection/hilt-android#not-supported)
## Way 1: Create an entry point
1. Create an entry point using the `@EntryPoint` annotation.

### Example

```
class ExampleContentProvider : ContentProvider() {

  @EntryPoint
  @InstallIn(SingletonComponent::class)
  interface ExampleContentProviderEntryPoint {
    fun analyticsService(): AnalyticsService
  }

  ...
}
```

### **RELATED QUESTION**
#### How to access an entry point that created with `@EntryPoint` annotation?

To access an entry point, use the appropriate static method from `EntryPointAccessors`. 

**NOTES** 

The parameter in `EntryPointAccessors` should be either the component instance or the `@AndroidEntryPoint` object that acts as the component holder. 

Please make sure that the component you pass as a parameter and the `EntryPointAccessors` static method both match the Android class in the `@InstallIn` annotation on the `@EntryPoint` interface.

Consider the following example (in next section).

##### Example
Continue the above example (in)

## Ref
[dependency injection in classes not supported by Hilt](https://developer.android.com/training/dependency-injection/hilt-android#not-supported)
