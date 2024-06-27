# setContent
## Defined in
ComponentActivity.kt
## package 
androidx.activity.compose   
## Syntax
public fun ComponentActivity.setContent(     
parent: CompositionContext? = null,     
content: @Composable () -> Unit ): 
Unit
androidx.activity.compose   
ComponentActivity.kt
## Parameter
### parent
The parent of content (in argument `content`).

It can be null. 

When it is NOT specified, it uses the default value null.

When it is specified as null, the root ui will be used.

### content
The content itself.

According the Syntax section, the value of argument content must be composable (sugar syntax with @Composable).

## Declaration
The declaration is as follows (if it is NOT edited or changed):

    public fun ComponentActivity.setContent(
        parent: CompositionContext? = null,
        content: @Composable () -> Unit
    ) {
        val existingComposeView = window.decorView
            .findViewById<ViewGroup>(android.R.id.content)
            .getChildAt(0) as? ComposeView
    
        if (existingComposeView != null) with(existingComposeView) {
            setParentCompositionContext(parent)
            setContent(content)
        } else ComposeView(this).apply {
            // Set content and parent **before** setContentView
            // to have ComposeView create the composition on attach
            setParentCompositionContext(parent)
            setContent(content)
            // Set the view tree owners before setting the content view so that the inflation process
            // and attach listeners will see them already present
            setOwners()
            setContentView(this, DefaultActivityContentLayoutParams)
        }
    }


