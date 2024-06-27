# ProfileContent
## Defined in
ProfileContent.kt

## Syntax
      @Composable
      fun ProfileContent(
          userProfile: LineProfile? = null,
          nonLoginHintText: String = stringResource(R.string.not_login)
      )

## Parameter
### userProfile
User profile in Line.

### nonLoginHintText
The hint text when user is NOT in login state.

## Declaration
The declaration is as follows (if it is NOT edited or changed):

      @Composable
      fun ProfileContent(
          userProfile: LineProfile? = null,
          nonLoginHintText: String = stringResource(R.string.not_login)
      ) {
          Column(
              verticalArrangement = Arrangement.Bottom,
              horizontalAlignment = Alignment.CenterHorizontally,
              modifier = Modifier
                  .fillMaxWidth()
                  .height(240.dp)
          ) {
              Box(
                  contentAlignment = Alignment.Center,
                  modifier = Modifier
                      .fillMaxWidth()
                      .height(96.dp)
              ) {
                  var shouldShowPlaceHolder by rememberSaveable { mutableStateOf(true) }
      
                  if (shouldShowPlaceHolder || userProfile == null) {
                      Image(
                          alignment = Alignment.Center,
                          painter = painterResource(R.drawable.default_avatar),
                          contentDescription = nonLoginHintText
                      )
                  }
      
                  userProfile?.let {
                      SubcomposeAsyncImage(
                          model = userProfile.pictureUrl,
                          contentDescription = userProfile.displayName,
                          alignment = Alignment.Center,
                          onSuccess = {
                              shouldShowPlaceHolder = false
                          },
                          loading = {
                              Box(
                                  contentAlignment = Alignment.Center
                              ) {
                                  CircularProgressIndicator()
                              }
                          },
                          modifier = Modifier
                              .fillMaxHeight()
                              .clip(CircleShape)
                      )
                  }
              }
      
              Text(
                  userProfile?.displayName ?: nonLoginHintText,
                  fontWeight = if (userProfile != null) FontWeight.Black else null,
                  color = if (userProfile != null) {
                      MaterialTheme.colorScheme.secondary
                  } else {
                      MaterialTheme.colorScheme.surfaceVariant
                  },
                  modifier = Modifier
                      .padding(vertical = 8.dp)
              )
          }
      }
