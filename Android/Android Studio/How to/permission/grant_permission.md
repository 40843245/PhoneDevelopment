# Grant Permission in Android Studio
## Way 1: Without code
1. In manifest file (by default, `AndroidManifest.xml`), use `<use-permission>` tag.

## Way 2: Programmtically
Use `requestPermissions` method.

### Example

```
val permissions = ArrayList<String>(1)
permissions.add("android.permission.SET_ALARM")
requestPermissions(permissions.toArray(Array<String>(5,{i->""})), PackageManager.PERMISSION_GRANTED)
```

