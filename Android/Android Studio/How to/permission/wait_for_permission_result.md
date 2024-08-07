# Wait for the result after granting permission in Android studio
## Way 1: Programmatically (`onRequestPermissionsResult` method)
Override `onRequestPermissionsResult` callback.

**NOTICE**
+ In Kotlin, when overriding a method, the method in super class must be called first. 

And thus, one has to write something like.

```
override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<String>,
        grantResults: IntArray
    ) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults)
        // Your code
    }
```

***deprecated***

+ The method is ***deprecated*** since the package `androidx.fragment.app.Fragment` is released according to the [article](https://stackoverflow.com/questions/66551781/android-onrequestpermissionsresult-is-deprecated-are-there-any-alternatives).


### Syntax

```
override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<String>,
        grantResults: IntArray
    )
```

For more details about syntax, see [`onRequestPermissionsResult` (Official Docs)](https://developer.android.com/reference/androidx/core/app/ActivityCompat.OnRequestPermissionsResultCallback#onRequestPermissionsResult(int,java.lang.String[],int[]))

### Example

```
override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<String>,
        grantResults: IntArray
    ) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults)
        if (requestCode == PackageManager.PERMISSION_GRANTED) {
            for(i in 0..permissions.size-1){
                val permission = permissions.get(i)
                Log.d(TAG,"Grant $permission successfully.")
            }
        }else{
            for(i in 0..permissions.size-1){
                val permission = permissions.get(i)
                Log.e(TAG,"NOT Grant $permission successfully.")
            }
        }
    }
```

In this example, if permission are successfully granted (i.e. `if (requestCode == PackageManager.PERMISSION_GRANTED)` is true), 

then the debug message "Grant $permission successfully." will be printed in Logcat for all permissions.

Otherwise (i.e. `if (requestCode == PackageManager.PERMISSION_GRANTED)` is NOT true),

then the error message "NOT Grant $permission successfully." will be printed in Logcat for all permissions.

## Way 2: Programmatically (`registerForActivityResult` method)
Use `registerForActivityResult` method 

**NOTES**

`registerForActivityResult` method is a new alternative of `onRequestPermissionsResult` method. Now `onRequestPermissionsResult` is ***deprecated***.

For use case, see 

+ [`registerForActivityResult` (stackoverflow)](https://stackoverflow.com/questions/66551781/android-onrequestpermissionsresult-is-deprecated-are-there-any-alternatives)

+ [`Get a result from an activity` (Official Docs)](https://developer.android.com/training/basics/intents/result)

For syntax, see

+ [`registerForActivityResult` (Official Docs)](https://developer.android.com/reference/androidx/activity/result/ActivityResultCaller#public-methods_1)


