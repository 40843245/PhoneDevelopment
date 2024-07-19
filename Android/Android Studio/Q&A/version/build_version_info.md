# build version info in Android Studio
## Q1: Get current SDK version in Android Studio
## A1: With code

You can use the field `SDK_INT` in `Build.VERSION` class.

`Build.VERSION.SDK_INT` will get an Integer that indicates the current SDK version that the project used.

Thus, one can easily check the SDK version by an `if` statement. Such as 

```
if(Build.VERSION.SDK_INT >= 13){
 //current SDK version is greater than or equal to 13.
}else{
  //current SDK version is less than 13.
}
```

### NOTICE
***Deprecated***
The field `SDK` in `Build.VERSION` class is deprecated in API level 15. Use `SDK_INT` instead.

### Ref
For more details, see [Build.VERSION.SDK_INT](https://developer.android.com/reference/android/os/Build.VERSION#SDK_INT)


