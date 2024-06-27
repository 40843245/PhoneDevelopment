# LoginButtonGroup
## package 
com.linecorp.linesdk.sample.ui.homeScreen
## Syntax
@ExperimentalMaterial3Api
@Composable
public fun LoginButtonGroup(
    loginViewModel: LoginViewModel,
    channelId: String,
    scopeList: List<Scope>,
    loginDelegateForLineLoginBtn: LoginDelegate,
    onSimpleLoginButtonPressed: (Intent) -> Unit
): Unit
com.linecorp.linesdk.sample.ui.homeScreen

## Parameter
### loginViewModel
Login UI.
### channelId
The channel ID of line bot for login.
### scopeList
Scope of permission of line bot.
### loginDelegateForLineLoginBtn
A callback that will be invoked once try to login.

Must be <b>LoginDelegate</b> type.

### onSimpleLoginButtonPressed
The intent (usually consist of one or more statements) will be executed once login successfully.

## Returned Type
Unit
