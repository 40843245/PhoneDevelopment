# PendingIntent
## Intro
A `PendingIntent` object is a wrapper around an `Intent` object. 

The primary purpose of a `PendingIntent` is to grant permission to a foreign application to 

use the contained Intent as if it were executed from your app's own process.

Major use cases for a `PendingIntent` include the following:

+ Declaring an intent to be executed when the user performs an action with your Notification (the Android system's `NotificationManager` executes the `Intent`).
+ Declaring an intent to be executed when the user performs an action with your App Widget (the Home screen app executes the `Intent`).
+ Declaring an intent to be executed at a specified future time (the Android system's `AlarmManager` executes the `Intent`).

## Ref
https://developer.android.com/reference/android/app/PendingIntent

## See Also
https://developer.android.com/guide/components/intents-filters?hl=en#PendingIntent
