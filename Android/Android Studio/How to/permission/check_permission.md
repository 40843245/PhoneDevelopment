# Check permission in Android Studio
## Way 1: Programmatically (`checkSelfPermission` method)
In code, use `checkSelfPermission` method.

### Syntax

```
checkSelfPermission(permission:String)
```

For more detail about syntax, see [checkSelfPermission (official Docs)](https://developer.android.com/reference/androidx/core/content/ContextCompat#checkSelfPermission(android.content.Context,%20java.lang.String))

### Example

```
val permission = "android.permission.SET_ALARM"
if(checkSelfPermission(permission) == PackageManager.PERMISSION_GRANTED){
  Log.d(TAG,"The {$permission} is GRANTED successfully.")
}else{
  Log.e(TAG,"The {$permission} is NOT GRANTED successfully.")
}
```

## Way 2: Programmatically (`checkPermission` method)
In code, use `checkPermission` method.

For use case and example, see [checkPermission (stackoverflow)](https://stackoverflow.com/questions/33540755/android-check-permission)

For syntax, see [checkPermission (official Docs)](https://developer.android.com/reference/android/content/Context#checkPermission(java.lang.String,%20int,%20int))
