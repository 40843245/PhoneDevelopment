# Button
## intro
A startup tutorial about Button.
## XML
In xml, we just have to use <Button> tag. Such as 

    <Button
                android:id="@+id/Button_1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Go to HomePage"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
## NOTICE
Notice that

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/1cc2da4c-1e3d-4fe7-a99b-6ef5e6ff56e8)

## Hierarchy of class 
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/d5af7d14-2f62-4b42-956b-9fff5909d53a)


## method (in Button class)
Here, I discuss the commonly used method of Button.
### setOnClickListener
#### syntax

    public void setOnClickListener(View.OnClickListener l)
    
#### intro
Set the callback function of onclick event. When the button is pressed, then l callback function will be called.

#### parameter

      l: onclick event callback function.

#### return value
      None

## method (in View class)
Here, I discuss the commonly used method of Button.
### setEnabled
#### syntax

    public void setEnabled(boolean enabled)
    
#### intro
Set it enabled state with parameter enabled

#### parameter

      enabled : true to enable. false to disable.

#### return value
      None

## Ref
https://developer.android.com/reference/android/widget/Button

https://www.tutorialspoint.com/how-to-jump-to-the-home-screen-of-the-app-using-a-button-in-android#:~:text=This%20example%20demonstrates%20how%20do%20I%20jump%20to,2%20%E2%88%92%20Add%20the%20following%20code%20to%20res%2Flayout%2Factivity_main.xml.

