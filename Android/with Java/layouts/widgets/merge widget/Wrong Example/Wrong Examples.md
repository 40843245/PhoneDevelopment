# Wrong Example about layouts in Android Studio.
## Objectives
In this article, I will notice about some details of layouts in Android Studio.

## NOTICE
1. Don't add


## Wrong Example (Examples with Unexpected results)
### Wrong Example 1
#### Java Code 
In the .../MainActivity.java of the zip file, available at:

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/Wrong%20Example/zip/project/Wrong_Example_1.zip

#### UI
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/457bdffe-5be1-4bed-a4b6-1cc5937cd4ea)

#### Expected UI
I expected that the text "textView1" appears just below the EditText "Elem1".

However, the text "textView1" appears next to and below the EditText "Elem4". (Shown as the above figure.)

### Wrong Example 2
#### Java Code 
In the .../MainActivity.java of the zip file, available at:

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/Wrong%20Example/zip/project/Wrong_Example_2.zip

#### UI
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/2188b7f6-3d21-4172-b855-0b18edfce8b8)

#### Expected UI
I expected that the text "textView1" appears just below the EditText "Elem1".

However, there are bugs while running.

## Ref
None, all of that are the result of I have tried.

### Wrong Example 2
#### Java Code 
In the .../MainActivity.java of the zip file, available at:

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/Wrong%20Example/zip/project/Wrong_Example_3.zip

#### UI
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/97450dec-df13-45c3-b922-41612a7c779d)


#### Expected UI
I expected that the text "textView1" appears just below the EditText "Elem1".

However,  the text "textView1" appears just right to the EditText "Elem4".

