# PendingIntent
## Intro
A `PendingIntent` object is a wrapper around an `Intent` object. 

The primary purpose of a `PendingIntent` is to grant permission to a foreign application to 

use the contained Intent as if it were executed from your app's own process.

Major use cases for a `PendingIntent` include the following:

+ Declaring an intent to be executed when the user performs an action with your Notification (the Android system's `NotificationManager` executes the `Intent`).
+ Declaring an intent to be executed when the user performs an action with your App Widget (the Home screen app executes the `Intent`).
+ Declaring an intent to be executed at a specified future time (the Android system's `AlarmManager` executes the `Intent`).

## Declaration by PendingIntent method

One must declare the intended component type when you create the `PendingIntent` by calling the respective creator method:

+ `PendingIntent.getActivity()` for an `Intent` that starts an `Activity`.
+ `PendingIntent.getService()` for an `Intent` that starts a `Service`.
+ `PendingIntent.getBroadcast()` for an `Intent` that starts a `BroadcastReceiver`.

## Specify mutability 

If your app targets Android 12 or higher, you must specify the mutability of each `PendingIntent` object that your app creates. 

To declare that a given `PendingIntent` object is mutable or NOT, use the `PendingIntent.FLAG_MUTABLE` or `PendingIntent.FLAG_IMMUTABLE` flag, respectively.

### See Aslo
For more information about how to specify mutability in PendingIntent in Android Studio, visit [specify mutability in PendingIntent](https://developer.android.com/guide/components/intents-filters?hl=en#DeclareMutabilityPendingIntent)


## See Also
https://developer.android.com/guide/components/intents-filters?hl=en#PendingIntent

## API Ref
https://developer.android.com/reference/android/app/PendingIntent


