# Spannable
## packages
android.text.Spannable
## inherit
Spanned
## type
interface
## public methods
    
    setSpan

    
### setSpan
#### intro
Set the settings about the span.
#### syntax

       public abstract void setSpan (Object what, 
                int start, 
                int end, 
                int flags)
                
 #### parameter 
 
      what : What object will be used?
      
      start : The index to start.
      
      end : The index to end.
      
      flags : The related settings about the what object.
      
 #### return value
      void
      
 ### removeSpan
 #### intro 
 Remove the span.
 #### syntax

       public abstract void setSpan (Object what)
                
 #### parameter 
 
      what : What object will be used?
      
 #### return value
      void
      
 ## Example
 See the example in the section "Examples (examples without bugs)" in the article.
 
 https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/textview/constructor/TextView.md
 ## Ref
 Android Official Docs.
 
 https://developer.android.com/reference/android/text/Spannable#setSpan(java.lang.Object,%20int,%20int,%20int)
 
 
  
