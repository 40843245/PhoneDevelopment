# OnError Listener in MediaPlayer

## Example
For more fully examples, see my projects in Github, available at 

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/VideoView/Project/zip.

### Example 1
When there are errors, the onError callback function will be called.

For more fully example, see my project VideoPlayer_3.zip in Github.

#### Part of code
        VideoView videoView_1;
        videoView_1.setOnErrorListener(new MediaPlayer.OnErrorListener()
        {
            @Override
            public boolean onError(MediaPlayer mp, int what, int extra)
            {
                textView_1.setText("");
                textView_1.append("ERROR!!! Can NOT play the media player.\n");
                return true;
            }
        });

        

### Example 2
When there are errors, the default behavour will be performed 

instead of calling onError callback function. 

Because onError callback function return false (according to my try and the official Docs, see the following figure.)

#### Note 
Note that

The default behavour may vary on different version of different devices.

In my device, there is a pop up window about error message in Android device 

and then jump into complete state, and thus calling onCompletion callback function.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/57cd47d2-6d6b-45c0-b56e-09fed8179a31)

For more fully example, see my project VideoPlayer_2.zip in Github.

#### Part of code
        VideoView videoView_1;
        videoView_1.setOnErrorListener(new MediaPlayer.OnErrorListener()
        {
            @Override
            public boolean onError(MediaPlayer mp, int what, int extra)
            {
                textView_1.setText("");
                textView_1.append("ERROR!!! Can NOT play the media player.\n");
                return false;
            }
        });

## Ref

VideoView:

https://developer.android.com/reference/android/widget/VideoView

