# Correct Example about layouts in Android Studio
## Correct Example
### Correct Example 1
#### Code
In the .../MainActivity.java of the zip file, available at

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/Correct%20Example/zip/project/Correct_Example_1.zip

#### Expected UI
The text "textView1" is just below to the EditText "Elem1". Shown as the following figure.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/ddb8e124-179c-4d20-948b-0848bcf77710)

#### UI

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/506e3235-7bbd-4655-a6ae-ed79c6bdc927)

#### Explanation
1. I nested a LinearLayout tag (id: LinearLayout_1)in an other LinearLayout tag(id: LinearLayout_root ) which is the root element of the UI.
2. I also set the orientation of LinearLayout_root as vertical by setting the attribute android:orientation as follows.

        android:orientation="vertical"
    

