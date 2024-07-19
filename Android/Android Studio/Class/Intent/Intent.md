# Intent
## Intro
An `Intent` object carries information that the Android system uses to determine which component to start 

(such as the exact component name or component category that should receive the intent).

## Type of Intent
+ Explicit intents
+ Implicit intents

### Explicit intents
#### Example

```
// Executed in an Activity, so 'this' is the Context
// The fileUrl is a string URL, such as "http://www.example.com/image.png"
val downloadIntent = Intent(this, DownloadService::class.java).apply {
    data = Uri.parse(fileUrl)
}
startService(downloadIntent)
```

For more details, see [intent and intent filter(official Docs)](https://developer.android.com/guide/components/intents-filters?hl=en#kotlin)

### Implicit intents
#### Diagram
![image](https://github.com/user-attachments/assets/fbd6f9b1-21ee-413d-8a80-2139d7c1a558)

#### Receiving an implicit intent
To publish which implicit intents your app can receive, declare one or more intent filters for each of your app components with an <intent-filter> element in your manifest file (By default, `AndroidManifest.xml`). Each intent filter specifies the type of intents it accepts based on the intent's action, data, and category. The system delivers an implicit intent to your app component only if the intent can pass through one of your intent filters.

**Warning** 

If an activity, service, or broadcast receiver in your app uses intent filters and doesn't explicitly set the value for android:exported, your app can't be installed on a device that runs Android 12 or higher.

###
For more details, see [Receiving an implicit intent(official Docs)](https://developer.android.com/guide/components/intents-filters?hl=en#Receiving)

#### Example

```
// Create the text message with a string.
val sendIntent = Intent().apply {
    action = Intent.ACTION_SEND
    putExtra(Intent.EXTRA_TEXT, textMessage)
    type = "text/plain"
}

// Try to invoke the intent.
try {
    startActivity(sendIntent)
} catch (e: ActivityNotFoundException) {
    // Define what your app should do if no activity can handle the intent.
}
```

For more details, see [intent and intent filter(official Docs)](https://developer.android.com/guide/components/intents-filters?hl=en#kotlin)
## Information
It contains these informations:

+ Component name (optional)
+ Action
+ Data
+ Category
+ Extras
+ Flags

### Component name
The name of the component to start.

If `Component name` is specified, `Intent` will be explicit so that one can deliver the intent only to the app component that is defined by `Component name`.

Otherwise (i.e. if `Component name` is NOT specified) , `Intent` will be implicit so that app component that is defined by other information of `Intent`.

### Action
A string that specifies the generic action to perform (such as view or pick).

You can specify your own actions for use by intents within your app (or for use by other apps to invoke components in your app), but you usually specify action constants defined by the Intent class or other framework classes.

For all available actions for an activity, see [Constant in Intent class (official Docs)](https://developer.android.com/reference/android/content/Intent)

### Data
The URI (a Uri object) that references the data to be acted on and/or the MIME type of that data. 

The type of data supplied is generally dictated by the intent's action. For example, if the action is ACTION_EDIT, the data should contain the URI of the document to edit.

When creating an intent, it's often important to specify the type of data (its MIME type) in addition to its URI. 

#### Example
For example, an activity that's able to display images probably won't be able to play an audio file, even though the URI formats could be similar. Specifying the MIME type of your data helps the Android system find the best component to receive your intent. However, the MIME type can sometimes be inferred from the URI—particularly when the data is a content: URI. A content: URI indicates the data is located on the device and controlled by a ContentProvider, which makes the data MIME type visible to the system.

#### Related method
To set only the data URI, call `setData()` in `Intent` class. 

To set only the MIME type, call `setType()` in `Intent` class. 

To set both, call `setDataAndType()` in `Intent` class. 

**NOTICE**

To set both, NEVER either call `setData()` then `setType()` or `setType()` then `setData()` since they each nullify the value of the other. **Always** use `setDataAndType()` instead.

### Category
A string containing additional information about the kind of component that should handle the intent. Any number of category descriptions can be placed in an intent, but most intents do not require a category.

#### Related method
+ To add a category, use `addCategory()` in `Intent` class.
+ To remove a category, use `removeCategory()` in `Intent` class.
+ To check the category exists in the `Intent` object, use `hasCategory()` in `Intent` class.

For all available category, see [Constant in Intent class (official Docs)](https://developer.android.com/reference/android/content/Intent)

### Extras
Key-value pairs that carry additional information required to accomplish the requested action. Just as some actions use particular kinds of data URIs, some actions also use particular extras.

#### Related method

+ To add extra data, use `putExtra()` in `Intent` class.
+ To remove extra data, use `removeExtra()` in `Intent` class.
+ To get extra data, use `getShortExtra()` in `Intent` class.
+ To copy extra data from other `Intent` object or `Bundle` object, use `putExtras()` in `Intent` class. See [`putExtras`](https://developer.android.com/reference/android/content/Intent#putExtras(android.content.Intent))

**Caution**
Do not use `Parcelable` or `Serializable` data when sending an intent that you expect another app to receive. 

If an app attempts to access data in a `Bundle` object but does not have access to the parceled or serialized class, the system raises a `RuntimeException`.

### Flags
metadata for the intent.

flags may instruct the Android system how to launch an activity (for example, which task the activity should belong to) and how to treat it after it's launched (for example, whether it belongs in the list of recent activities).

For more information, see the `setFlags()` method.

## Nested PendingIntent
### Diagram
![image](https://github.com/user-attachments/assets/5e29ea91-28f1-4f6d-8c69-bce63a892d3e)
