# grant permission for runtime in Android Studio
## Way 1 (`uses-permission` in manifest file)
1. In manifest file (by default, `AndroidManifest.xml`), use the tag `uses-permission`. Such as

```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```
For more details about the permission, see [overview of permission in Android Studio](https://developer.android.com/guide/topics/permissions/overview)


