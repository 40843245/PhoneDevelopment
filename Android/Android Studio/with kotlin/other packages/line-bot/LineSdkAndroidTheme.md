# LineSdkAndroidTheme
## Defined in
LineSdkAndroidTheme.kt

## Syntax
@Composable
fun LineSdkAndroidTheme(
    useDarkTheme: Boolean = isSystemInDarkTheme(),
    dynamicColor: Boolean = Build.VERSION.SDK_INT >= Build.VERSION_CODES.S,
    content: @Composable () -> Unit
)
## Parameter
### useDarkTheme 
A boolean value that determines the theme will be a(n) dark theme.

If it is specified to true, the dark theme will be used. Otherwise, the dark theme will NOT be used.

If it is NOT specified, the returned value of `isSystemInDarkTheme()` will be used.

### dynamicColor
A boolean value that indicates the color is dynamic, or not(more exactly to say, the color is dynamically changed at run time, or not).

If it is specified to true, the color will be dynamic. Otherwise, the color will NOT be dynamic.

If it is NOT specified, the returned value of ` Build.VERSION.SDK_INT >= Build.VERSION_CODES.S` will be used.

### content
The content itself.

