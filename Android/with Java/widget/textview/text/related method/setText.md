# setText -- Set the content of the text.
## Step
To set the content of the text, we have to access the TextView of LinearLayout tag in activity_main.xml, then

change the text by the invocation of the method setText.

## part 1
For the first part (access the TextView), I have mentioned it in the file setTextColor.md.

## part 2

### syntax
In the method setText, there are three major overloaded methods. Here, in this article, I will disccuss the third overloaded method.
  
  public void setText (CharSequence text, 
                      TextView.BufferType type)
                      
  public final void setText (int resid, 
                TextView.BufferType type)
                
   public final void setText (char[] text, 
                int start, 
                int len)
                
### syntax
In the third type, the text must be specified while the start and len can be null.

In C++ style,

    public final void setText (char[] text)
                
    public final void setText (char[] text, 
                int start, 
                int len)
                
### parameter 
    text : a char array represent the text to ready to display.
    
    start : the index of parameter text to start to display.
    
    len : the length of text will be displayed.

### NOTE

1. If both parameters start and len are NOT specified, then the start is assumed to 0 and len is assumed to length of the parameter text.

In this case, all chars of the parameter text will be displayed.

2. The parameter text can NOT be null. Otherwise, the exception (NullPointerException) throws.

3. If either start + len > the length of the parameter text or start + len < 0, then the exception (IndexOutOfBoundsException) throws.

If start + len == 0, then of course, NO text will display.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/5fcfa1c2-bedf-41aa-9666-d061574b01a5)

### return value    
    void
              
## Ref

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/c1206ef7-efbf-447a-88f3-16e81d7fb2f4)

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/159489b9-c658-4a34-b12f-baf86a147349)

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/b0480a21-0f4b-46f0-94e4-94d71f77f2e5)

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/ec71a70f-e7e8-49a9-be9e-4ec51cebccbc)

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/23785090-cd47-4c06-af56-bb51f30a6039)

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/77675714-e3d0-40b4-85cc-2e5344a3b44e)


All above figures are screenshots in the Android Official Docs.

https://developer.android.com/reference/android/widget/TextView#setText




