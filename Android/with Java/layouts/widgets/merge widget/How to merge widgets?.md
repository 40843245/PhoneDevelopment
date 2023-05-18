# Q: How to merge widgets with Java code in Android Studio?
## Description
Such as see a text and a button together which to the text in the project.

Figure 1:

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/da8eb545-7b13-4ab3-9d5a-59b16c6d966b)

## Answer
It is very simple. But it requires the basic concept of layouts and widgets.

To do this with Java code,

first, one needs to create widgets then adding them into different layouts.

Finally, merge these layouts into a layout as the root layout. (For example, see Example 1.)

The tree structure of the widgets and layout and major step is shown as following figure.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/5e8e26e1-e060-4a00-a762-a62f955ce50c)

## NOTICE
NOTICE that 

1. It is <b>impossible</b> to merge lots of widgets in 1 layout.

If one try to do so with setView method , then the latest widget will override the previous widgets. (See Example 2.)

## Example
### Example 1 (Example with Epected results)
#### Java code and XML file 
Shown in the project which is in zip file.

The Java code file is mainly defined .../MainActivity.java .

The XML file file is mainly defined .../res/layout/activity_main.xml .

The zip file in GitHub is available at:

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/zip/project/FrameLayout_Project_1_v1.zip

#### UI 

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/da8eb545-7b13-4ab3-9d5a-59b16c6d966b)

### Example 2 (Example with Unexpected results)
#### Java code and XML file
Shown in the project which is in zip file.

The zip file in GitHub is available at:

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/zip/project/FrameLayout_Project_1_v2.zip

#### UI
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/0399e8e7-623c-4767-8c47-30f8245f5f1d)

### Example 3 (Example with Unexpected results)
#### Java code and XML file
Shown in the project which is in zip file.

The zip file in GitHub is available at:
https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/layouts/widgets/merge%20widget/zip/project/FrameLayout_Project_1_v3.zip

#### UI

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/da8eb545-7b13-4ab3-9d5a-59b16c6d966b)

## Observation
With Example 1 and Example 3, we can find the fact that it is impossible to put them in 1 layout, 

but it is possible to put them in many different layouts and seems to combine them (visually).

And the fact that it is simple to swap the widgets (visually), just swap the layouts (for more fully understand, I recommend you to compare the files in the project in the zip file, in Example 1 and Example 3.)


## Ref
None




