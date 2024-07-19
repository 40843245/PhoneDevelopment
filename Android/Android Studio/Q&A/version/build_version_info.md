# build version info in Android Studio
## Q1: Get current SDK version in Android Studio
## A1: With code

You can use the field `SDK_INT` in `Build.VERSION` class.

`Build.VERSION.SDK_INT` will get an Integer that indicates the current SDK version that the project used.

### NOTICE
***Deprecated***
The field `SDK` in `Build.VERSION` class is deprecated in API level 15. Use `SDK_INT` instead.

### Ref
For more details, see [Build.VERSION.SDK_INT](https://developer.android.com/reference/android/os/Build.VERSION#SDK_INT)


