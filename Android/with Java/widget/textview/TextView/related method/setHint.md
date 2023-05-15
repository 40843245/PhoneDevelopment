# setHint -- Set hint message (only shows when the text of TextView is empty.)
## Objective
Tell you how to what is the effect of the method setHint.

## intro
Set the hint message of the TextView. 

The hint message will display iff the text of TextView is empty.

## syntax

    setHint(CharSequence hint)
    
    or
    
    setHint(int resid)
    
### setHint(CharSequence hint)
#### parameter 
    
    hint : The hint message of the TextView.
 #### return value 
    void
    
### setHint(int resid)
#### parameter 
    
    resid : The id of resource as the hint message of the TextView.
    
    It must exists in the <resource> tag in other .xml file.
    
 #### return value 
    void
 ## Examples
 ### Examples (with hint message display)
 
 Note that the comments in these statements.
 
        //textView1.setText(word1);

        //textView1.append("\n");

        //textView1.append(word2);
        
In this example, you will see the hint message "This is a hint" displays on the TextView when running the application.  

Figure to illustrate the result.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/926a3acf-d852-4338-9f83-c873ba414e92)

Exanple of full code
 
     @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);

        LinearLayout my_root = (LinearLayout) findViewById(R.id.linearLayout);

        LinearLayout layout = new LinearLayout(this);
        layout.setOrientation(LinearLayout.VERTICAL);

        LinearLayout.LayoutParams params =
                new LinearLayout.LayoutParams(
                        980
                        ,1200
                        ,120
                );

        TextView textView1 = new TextView(this);
        Spannable word1=new SpannableString(getResources().getString(R.string.word1));
        Spannable word2=new SpannableString(getResources().getString(R.string.word2));
        word1.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.lightGreen)),0,word1.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);

        word2.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.orange)),0,word2.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);


        //textView1.setText(word1);

        //textView1.append("\n");

        //textView1.append(word2);


        textView1.setHint("This is a hint.");

        layout.addView(textView1);
        my_root.addView(layout);
    }
 
 ### Examples (without display hint message)

In this example, you will NOT see the hint message "This is a hint" displays on the TextView when running the application.  

Figure to illustrate the result.

 ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/3b526ef6-8984-4839-9f57-180835d13042)
 
 Example of full code
    
        @Override
        protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        LinearLayout my_root = (LinearLayout) findViewById(R.id.linearLayout);

        LinearLayout layout = new LinearLayout(this);
        layout.setOrientation(LinearLayout.VERTICAL);

        LinearLayout.LayoutParams params =
                new LinearLayout.LayoutParams(
                        980
                        ,1200
                        ,120
                );

        TextView textView1 = new TextView(this);
        Spannable word1=new SpannableString(getResources().getString(R.string.word1));
        Spannable word2=new SpannableString(getResources().getString(R.string.word2));
        word1.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.lightGreen)),0,word1.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);

        word2.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.orange)),0,word2.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);


        textView1.setText(word1);

        textView1.append("\n");

        textView1.append(word2);


        textView1.setHint("This is a hint.");

        layout.addView(textView1);
        my_root.addView(layout);
    }

 
 ## ref
 From Android Official Docs.
 
https://developer.android.com/reference/android/widget/TextView#setHint(java.lang.CharSequence)

