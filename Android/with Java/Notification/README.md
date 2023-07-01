# Send Notification in Android with Android Studio.
## Objective
In this article, I will discuss that how to send notification.
## Method
Notification Channel + NotificationCompat.Builder + Notification Manager => A whole Notification

Step 1:

Notification Channel

Create an instance, Notification Channel with the class NotificationChannel. Then set it.

Step 2: 

Notification Builder

Create a instance, Notification Builder with class NotificationCompat.Builder. Set it.

Then call the method build() to build an instance, notification with class notification.

Step 3:

Notification Manager

Create a instance, Notification Manager with class NotificationManager.

Then add the instance, notification channel (which is created in Step 1) to it.

Step 4:

Permission

Check the following permission. If it is NOT granted, grant it at runtime.

        android.Manifest.permission.POST_NOTIFICATIONS

You can check 1 permission through 1 statement.

    ActivityCompat.checkSelfPermission(this, android.Manifest.permission.POST_NOTIFICATIONS) != PackageManager.PERMISSION_GRANTED

You can grant lots of permissions through only 1 statement.

        ActivityCompat.requestPermissions(this,
                        new String[]
                                {
                                        android.Manifest.permission.POST_NOTIFICATIONS
                                },
                        0
                );

  For more details, see my other note in Github or official Docs.

  Step 5: 

  Notify

  Finally, we just notify it through the method notify.

        notificationManager.notify(
                    "123",NotificationManagerCompat.IMPORTANCE_HIGH,
                    notification
            );

## NOTICE
Notice that

In Android Studio, it is neccessary to call method notify in Exception handling block.

That is, it is neccessary

      try
      {
        notificationManager.notify(
                    "123",NotificationManagerCompat.IMPORTANCE_HIGH,
                    notification
            );
      }
      catch(Exception exception)
      {
        //Do exception handling
      }

For more details, see zip file in Project section.
## Project 
See my zip Notitification_1.zip in Github.

### Part of code

        try
        {
            NotificationChannel notificationChannel = new NotificationChannel(
                    CHANNEL_ID,
                    "Followers",
                    NotificationManager.IMPORTANCE_HIGH
            );
            notificationChannel.setLightColor(Color.GREEN);
            NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
                    .setSmallIcon(R.drawable.ic_launcher_background)
                    .setContentTitle("Title 1")
                    .setContentText("Content 1")
                    .setChannelId(CHANNEL_ID)
                    .setPriority(NotificationCompat.PRIORITY_DEFAULT);

            Notification notification = builder.build();
            NotificationManager notificationManager=(NotificationManager)getSystemService(Context.NOTIFICATION_SERVICE);
            notificationManager.createNotificationChannel(notificationChannel);

            textView_2.setText("");
            textView_2.append(notification.toString()+"\n");

            if (ActivityCompat.checkSelfPermission(this, android.Manifest.permission.POST_NOTIFICATIONS) != PackageManager.PERMISSION_GRANTED)
            {
                textView_1.setText("");
                textView_1.append("ERROR!!! POST_NOTIFICATIONS permission NOT granted successfully."+"\n");

                ActivityCompat.requestPermissions(this,
                        new String[]
                                {
                                        android.Manifest.permission.POST_NOTIFICATIONS
                                },
                        0
                );
            }
            textView_3.setText("");
            textView_3.append(String.valueOf(notificationManager.areNotificationsEnabled()));

            notificationManager.notify(
                    "123",NotificationManagerCompat.IMPORTANCE_HIGH,
                    notification
            );
            textView_1.setText("");
            textView_1.append("Notified\n");
        }
        catch (Exception exception)
        {
            textView_1.setText("");
            textView_1.append(exception.toString());
            textView_1.append("\n");
        }

### Explanation

#### Detailed explanation

1.

          NotificationChannel notificationChannel = new NotificationChannel(
                    CHANNEL_ID,
                    "Followers",
                    NotificationManager.IMPORTANCE_HIGH
            );

In above part of code, we create an instance with class NotificationChannel named notificationChannel

where 
      
      CHANNEL_ID refers channel ID. It should be an integer.
      "Followers" refers the channel name.
      NotificationManager.IMPORTANCE_HIGH refers the importance of notification.

2.

      notificationChannel.setLightColor(Color.GREEN);

  In above part of code, we set the light color of notification channel as GREEN.

3.
  
         NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
                    .setSmallIcon(R.drawable.ic_launcher_background)
                    .setContentTitle("Title 1")
                    .setContentText("Content 1")
                    .setChannelId(CHANNEL_ID)
                    .setPriority(NotificationCompat.PRIORITY_DEFAULT);

 In above part of code, we create an instance with class NotificationCompat.Builder named builder

 where 
 
    the builder refers the Context this.

    CHANNEL_ID refers the channel ID.

In same statement, we set the small icon as R.drawable.ic_launcher_background. Set the title of notification as "Title 1".

Set the text of context as "Content 1". 

Set channel ID as CHANNEL_ID.

Set the priority of notification as NotificationCompat.PRIORITY_DEFAULT which an integer type.

4.

        Notification notification = builder.build();

We create a notification with the method of builder.

5.

       NotificationManager notificationManager=(NotificationManager)getSystemService(Context.NOTIFICATION_SERVICE);

We create a instance, notification manager to manager the notification.

6.

        notificationManager.createNotificationChannel(notificationChannel);

We add notificationChannel to notificationManager.

7.

            if (ActivityCompat.checkSelfPermission(this, android.Manifest.permission.POST_NOTIFICATIONS) != PackageManager.PERMISSION_GRANTED)
            {
                textView_1.setText("");
                textView_1.append("ERROR!!! POST_NOTIFICATIONS permission NOT granted successfully."+"\n");

                ActivityCompat.requestPermissions(this,
                        new String[]
                                {
                                        android.Manifest.permission.POST_NOTIFICATIONS
                                },
                        0
                );
            }

We create a check following permission. Grant it if not granted.

      android.Manifest.permission.POST_NOTIFICATIONS

8.

        notificationManager.notify(
                    "123",NotificationManagerCompat.IMPORTANCE_HIGH,
                    notification
            );
  

We send the notify as notification with notificationManager.

9. 

        catch (Exception exception)
        {
            textView_1.setText("");
            textView_1.append(exception.toString());
            textView_1.append("\n");
        }

If there is an Exception thrown, then these statement are executed. Thus, set the textView_1 as exception.

## Link to Project

https://github.com/40843245/PhoneDevelopment/tree/main/Android/with%20Java/Notification/project/zip

## Ref

