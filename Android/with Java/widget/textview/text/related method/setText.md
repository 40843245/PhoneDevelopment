# setText -- Set the text 
## Step
To set the text, you have to access the TextView in LinearLayout tag in the file activity_main.xml.

Then change the text color of TextView 

## Part 1
To do the first part (access the TextView in LinearLayout tag in the file activity_main.xml), you can either

    1. XML (Create a xml tag)
    
    ,or
    
    2. XML + Java ( Create a xml tag + change it in Java)
 
### way 1

Create a xml tag in activity_main.xml which defaults to be located in 

    .../res/layout/activity_main.xml

(Suppose that the layout of the project refers this file.)

For more fully about these details, see the following figure.

In the following figure, the red pen highlights the directory of activity_main.xml


![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/033c2b4c-2344-43a2-8beb-f6266429a958)

      
 ### way 2

  Create a xml tag in activity_main.xml (as we discussed above) then change it with Java 
   
  through modifying the exisiting tag in the file named MainActivity.java which defaults to be located in 
   
      .../<your-application-name>/MainActivity.java
  
  where 
     
  <your-application-name> is the name of your application in the project.
    
  
  To change the color of text, you must access TextView instance.
    
  You can either access the existing TextView instance with either id or create a new one. Then change it.
 

  Again, for more fully about these details, see the following figure.

  In the following figure, the red pen highlights the directory of MainActivity.java
  
  ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/3284431a-f087-47d6-97ba-e31c0da7c61e)

## 
    
    
### NOTE
   
It is critical to pay lots of attention to these notes.
    
You always have to check lots of things once, before building the project. 
    
I just list things about this article.
    
1. Check the xml file for layout.
    
   The file for layout should be a xml file (file extension with .xml).
    
    Additionally, it should be placed in the directory.
    
    .../res/layout
    
    Finally, the file name should match R.layout.<filename> in the statement in MainActivity.java .
    
    The following figures illustrate the example.
    
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/ec0c1347-ef27-47e2-b40e-4c5ed8a5984e)
    
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/f7ef4ec1-b11f-478c-9552-36a3413a19eb)

    
 2. Check the id of LinearLayout tag in activity_main.xml .

    The id of LinearLayout tag in activity_main.xml should match the R.id.<idName> in MainActivity.java .
    
    (If you access the existing TextView with id, you also have to check the id of TextView.)
    
    Again, the following figures illustrate the example.
    
    ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/92f25ca6-3286-4072-9604-770233103698)
    
    ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/9f5987cf-4fdb-4a0a-a31e-642b6fa54638)
    
## Part 2 
    
After we access the TextView instance, we can change the color of the TextView by invoking the method.
    
    tx.setTextColor(ContextCompat.getColor(this, R.color.orange));
 
### syntax
    
The method setTextColor overloads two methods.
    
    setTextColor(ColorStateList colorStateList)
    
    or 
    
    setTextColor(int[][] state, int[] color)
    
### parameter
In the method setTextColor(ColorStateList colorStateList),
    
    colorStateList: It should be a color defined in colors.xml which defaults to be located in the directory.
    
    .../res/values/colors.xml
    
As shown in the following figure.
    
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/b445a58b-a86d-4db0-9557-8e444edaef4b)
    
and we should get the ColorStateList instance with the invocation of the method such as 
    
ContextCompat.getColor(this, R.color.orange)

We skip the second method setTextColor(int[][] state, int[] color).
    
### return value
    void 
    
## Ref
For more details of the method setTextColor, see the Android Official Docs.
    
https://developer.android.com/reference/android/widget/TextView#setTextColor(android.content.res.ColorStateList)
    
For the way to change the text of color, see the replies on StackOverflow, especially about the reply.
    
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/38e56500-839b-47a7-a80e-ce3358c43357)

    
 https://stackoverflow.com/questions/5271387/how-can-i-get-color-int-from-color-resource
    
    

    

    
