# Check Version
Use Macros in Build class

## Macro
I will list commonly used macro.

Build.VERSION.SDK_INT

        an integer which refers version of Android SDK of software on device which is running on.

Build.VERSION.SDK

        a string which refers version of Android SDK of software on device which is running on.

        It is a string type of Build.VERSION.SDK_INT.

## Example
In the zip file,

### Code
        // Check if we're running on Android 5.0 or higher
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP)
            // Version >= 5.0
        {
            // Apply activity transition
        } else
            // Version < 5.0
        {
            // Swap without transition
        }
### Explanation 
The above code check the software of currently running device >= Android 5.0


## Ref
From Official Docs,

https://developer.android.com/reference/android/os/Build
        

