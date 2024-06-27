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




