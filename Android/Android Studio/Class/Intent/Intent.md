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



