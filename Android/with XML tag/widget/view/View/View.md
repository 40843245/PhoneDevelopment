# View tag in XML file in Android Studio
## Objectives
1. How to create a View with View tag in XML file in Android Studio?
2. Effect of View tag in XML file in Android Studio.

## create 
To create a view in Android Project in XML file, simply use View tag.(Look at NOTE section and example 1. in Example section)

## NOTE 
View tag is self-closing. i.e. it works with the following rule. (At least, I am sure that it can work)

    <View 
    />
    
Instead of these
    
      <View> 
      </View>
      
Again, I remind that 

    <View 
    />
works for me.

But, 

      <View> 
      </View>
      
does NOT work for me. It will cause a bug when running the project and thus cause to display a white empty view.
    
## Example
### Example 1
#### XML file 
In my project, the content of the XML file
    
    .../res/layout/view_1.xml
   
is shown as follows.

    <?xml version="1.0" encoding="utf-8"?>
    <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <LinearLayout
            android:id="@+id/view_LinearLayout_1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            >
        <View
            android:id="@+id/view_1_view_1"
            android:layout_width="50dp"
            android:layout_height="100dp"
            android:background="@color/yellow"
            tools:ignore="MissingConstraints"
            />
        <Button
            android:id="@+id/view_1_button_1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="A view_1_button_1"
            />
        </LinearLayout>
    </androidx.constraintlayout.widget.ConstraintLayout>
    
#### UI 
In my project, the UI should looks like this

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/0c0b3f10-7435-49a7-99ff-19015addf98e)


## Ref

Simply hint to startup in StackOverflow:

https://stackoverflow.com/questions/32766869/how-could-i-use-a-view-node-in-android-xml-layout-file

Android Official Docs:

https://developer.android.com/reference/android/view/View
