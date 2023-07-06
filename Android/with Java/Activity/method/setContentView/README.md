# Activity.setContentView
## class
In Activity class.
## intro
Set the activity content to an explicit view or from layout resource ID.
## syntax
    void setContentView(View view)
    
    setContentView(int layoutResID)
## setContentView(View view)
### parameter
    view : the view as content to be set to activity.

### return value
    None

## setContentView(int layoutResID)
### parameter
    layoutResID : the resource layout ID corresponds the view as content to be set to activity.

### return value
    None

## Example 
### Example 1 
#### Code
    setContentView(R.layout.activity_1);
#### Screenshot
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/5d8fcf23-7737-4d60-b400-f95539808f82)

The part of structure of the project.

#### Explanation
The following statement, the content of view will be set to activity_1.xml which is located in ../res/layout directory. (Shown as the above screenshot.)
        
        setContentView(R.layout.activity_1);
    
## Ref
https://developer.android.com/reference/android/app/Activity
    
