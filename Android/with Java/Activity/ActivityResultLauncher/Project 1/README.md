# ActivityResultLauncher
## Abstract
I take my learning as this article. I hope this article can help you as readers and me in the future.


## Objectives
In this article, teach you how to view image with file picker in Android device? 

With the project as an example, you will learn how to
    
      1. start an activity with class ActivityResultLauncher 
      2. open a file picker.
      3. select an image and display them.

You will learn basic usage of these class

    1. ActivityResultLauncher
    2. Intent
    3. ActivityResultCallback
    
## Prequisite

    1. concept of OOP.
    2. basic concept of Android Studio and layout of UI.
    3. ImageView

## Project
### Code
#### Partial Code in MainActivity
        Intent intent;
        ActivityResultLauncher<Intent> activityResultLauncher;
        int REQUEST_CODE = 10;
        
        intent = new Intent(Intent.ACTION_GET_CONTENT);
        intent.setType("image/jpg");
        intent.putExtra(Intent.EXTRA_LOCAL_ONLY, true);

        activityResultLauncher = registerForActivityResult(
                new ActivityResultContracts.StartActivityForResult(),
                new ActivityResultCallback<ActivityResult>()
                {
                    @Override
                    public void onActivityResult(ActivityResult result)
                    {
                        if (result.getResultCode() == Activity.RESULT_OK)
                        {
                            Intent data = result.getData();
                            Uri dataUri = data.getData();

                            ImageView imageView = findViewById(R.id.ImageView_1);
                            imageView.setImageURI(dataUri);

                            textView_2.append("uri:"+dataUri.toString()+"\n");
                            textView_2.append("uri.getPath():"+dataUri.getPath()+"\n");
                        }
                    }
                });
        activityResultLauncher.launch(intent);
### Explanation
#### Simple Explanation
In the above code,

we use the class ActivityResultLauncher<Intent> to create an activity.

Then invoke the method launch to launch the activity with intent.

To determine tasks what to do after the activity finishes, we override the method onActivityResult(ActivityResult result)

in the instance with new ActivityResultCallback<ActivityResult>().

#### Detailed Explanation

After activity finishes, the callback onActivityResult(ActivityResult result) will be invoked.

The method call result.getResultCode() will get the status of result (it should return with int type).

For more details, see my other note in Github.


