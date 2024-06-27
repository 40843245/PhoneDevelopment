# LoginButtonGroup
## Defined in 
LoginButtonGroup.kt

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

## Declaration
The declaration is as follows (if it is NOT edited or changed):

    @ExperimentalMaterial3Api
    @Composable
    fun LoginButtonGroup(
        loginViewModel: LoginViewModel,
        channelId: String,
        scopeList: List<Scope>,
        loginDelegateForLineLoginBtn: LoginDelegate,
        onSimpleLoginButtonPressed: (Intent) -> Unit
    ) {
        LazyColumn(
            horizontalAlignment = Alignment.CenterHorizontally,
            verticalArrangement = Arrangement.Center,
            modifier = Modifier
                .fillMaxHeight()
                .width(320.dp)
                .padding(
                    start = 32.dp,
                    end = 32.dp
                )
        ) {
            item {
                val context = LocalContext.current
                val isLogin by loginViewModel.isLoginFlow.collectAsState()
    
                LineLoginButton(
                    channelId,
                    modifier = Modifier
                        .fillMaxWidth(),
                    loginDelegate = loginDelegateForLineLoginBtn,
                    handleLoginResult = loginViewModel::processLoginResult
                )
    
                ApiDemoButton(
                    "login",
                    modifier = Modifier
                        .fillMaxWidth(),
                    enabled = !isLogin
                ) {
                    val intent = loginViewModel.createLoginIntent(
                        context,
                        channelId,
                        scopeList
                    )
                    onSimpleLoginButtonPressed(intent)
                }
    
                ApiDemoButton(
                    "web login",
                    modifier = Modifier
                        .fillMaxWidth(),
                    enabled = !isLogin
                ) {
                    val intent = loginViewModel.createLoginIntent(
                        context,
                        channelId,
                        scopeList,
                        onlyWebLogin = true
                    )
                    onSimpleLoginButtonPressed(intent)
                }
    
                ApiDemoButton(
                    "logout",
                    modifier = Modifier
                        .fillMaxWidth(),
                    enabled = isLogin
                ) {
                    loginViewModel.logout()
                }
    
                ApiDemoButton(
                    "Api List Page",
                    modifier = Modifier
                        .fillMaxWidth(),
                    enabled = isLogin,
                    emphasize = true
                ) {
                    ApiListActivity.start(context)
                }
            }
        }
    }
