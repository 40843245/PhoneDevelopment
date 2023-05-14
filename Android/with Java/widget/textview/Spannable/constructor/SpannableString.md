# Spannable
## packages
java.lang.Object
 
android.text.SpannableString

## inherit
CharSequence, GetChars, Spannable
## type
class 
## public constructor 
### intro
The SpannableString class handles the string for spannable object.

### syntax
      public SpannableString (CharSequence source)
                
 ### parameter 
     source : The source text.
     
 ### return value
      SpannableString
      
 ### NOTICE 
 Notice that the parameter source must be in resource tag (such as it can be an item of the resource tag in .../res/values/strings.xml).
 
 It can NOT be a string.
 
 More precisely to say, it is NOT allowed in the following example.
 
      new SpannableString("Hello");
      
Instead of this, we have to get resources such as the following example and figure.

      new SpannableString(getResources().getString(R.string.word1));
      
 ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/4fe56391-c58e-40f0-b9a2-45ca5a297693)

 
 
 ## Example
 See the example in the section "Examples (examples without bugs)" in the article.
 
 https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/textview/constructor/TextView.md
 ## Ref
 Android Official Docs.
 
https://developer.android.com/reference/android/text/SpannableString
 
 
  
