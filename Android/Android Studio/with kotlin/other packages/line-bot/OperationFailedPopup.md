# OperationFailedPopup
## Syntax
    
    @Composable
    fun OperationFailedPopup(
        content: String,
        modifier: Modifier = Modifier,
        onDismiss: () -> Unit = {}
    )
    
## Parameter
### content
The content of message on popup that will be displayed when operation failed.

### modifier
The modifier of popup.

### onDismiss
The callback that will be invoked once the function is dismissed.

## Declaration
The declaration is as follows (if it is NOT edited or changed):

    @Composable
    fun OperationFailedPopup(
        content: String,
        modifier: Modifier = Modifier,
        onDismiss: () -> Unit = {}
    ) {
        AlertDialog(
            onDismissRequest = onDismiss,
            text = {
                Text(
                    text = content,
                    style = MaterialTheme.typography.bodyLarge
                )
            },
            confirmButton = {
                TextButton(onClick = onDismiss) {
                    Text(stringResource(R.string.ok))
                }
            },
            modifier = modifier
        )
    }
