# OnError Listener in MediaPlayer

## Example
For more fully examples, see my projects in Github, available at 

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/VideoView/Project/zip.

### Example 1
For more fully example, see my project in Github.

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
