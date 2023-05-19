# Q: How to scale size of text in Spannable?
# A:
It is <b>possible</b> to set the relative size of text in Spannable.

It is <b>impossible</b> to set the absolute size of text in Spannable.

That is, you can scale the size of text in Spannable.

Just create a scaled size of text (it can be done with RelativeSizeSpan class)

,then set the Spannable to it (it can be done with setSpan method).

Look at the following statements.

            float proportion;
            Spannable spannable_temp;
            
            proportion = 2f ;
            spannable_temp=new SpannableString("spannable_temp");
            
            spannable_temp.setSpan(new RelativeSizeSpan(proportion)
                    ,0
                    ,spannable_temp.length()
                    ,Spannable.SPAN_EXCLUSIVE_EXCLUSIVE
                    );


It is scale up the Spannable named spannable_temp by 2.

## Ref
Thanks to the reply on the StackOverflow. I knew the RelativeSizeSpan class from it.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/d11f0cec-64cc-4430-a041-2892e90cf170)

https://stackoverflow.com/questions/16335178/different-font-size-of-strings-in-the-same-textview#:~:text=Use%20a%20Spannable%20String%20String%20s%3D%20%22Hello%20Everyone%22%3B,color%20TextView%20tv%3D%20%28TextView%29%20findViewById%20%28R.id.textview%29%3B%20tv.setText%20%28ss1%29%3B


Android Official Docs:

https://developer.android.com/reference/android/text/style/RelativeSizeSpan




