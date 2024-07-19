# Intent
## Intro
An `Intent` object carries information that the Android system uses to determine which component to start 

(such as the exact component name or component category that should receive the intent).

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

To set only the data URI, call `setData()` in `Intent` class. 

To set only the MIME type, call `setType()` in `Intent` class. 

To set both, call `setDataAndType()` in `Intent` class. 

