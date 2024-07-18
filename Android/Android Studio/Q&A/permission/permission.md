# permission for runtime in Android Studio
## Q1: Grant permission for runtime in Android Studio.
## A1:
### Way 1: (`uses-permission` in manifest file)
To grant permission at runtime, one can add the tag `uses-permission` in manifest file (by default, `AndroidManifest.xml`). Such as

```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```
For more details about the permission, see [overview of permission in Android Studio](https://developer.android.com/guide/topics/permissions/overview)

## Q2: Define custom permission in Android Studio.
## A2:
### Way 1: (`permission` in manifest file)
To define custom permission at runtime, one can add the tag `permission` in manifest file (by default, `AndroidManifest.xml`). Such as

```
    <permission
      android:name="com.example.myapp.permission.DEADLY_ACTIVITY"
      android:label="@string/permlab_deadlyActivity"
      android:description="@string/permdesc_deadlyActivity"
      android:permissionGroup="android.permission-group.COST_MONEY"
      android:protectionLevel="dangerous" />
```

For more details about how to use `permission` tag , see [`permission` tag in Android Studio](https://developer.android.com/guide/topics/permissions/defining)

