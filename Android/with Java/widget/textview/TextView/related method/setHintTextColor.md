# setHintTextColor -- Set the color of hint message
## intro
Set the color of hint message.
## syntax
    setHintTextColor(ColorStateList colors)
    setHintTextColor(int color)
### setHintTextColor(ColorStateList colors)
#### parameter 
    colors : It must be a ColorStateList instance. It determines the color of hint message of the TextView.
#### return value
    void
### setHintTextColor(int color)
#### parameter 
    color : It must be an integer. 
    
    It sets the color of the hint text for all the states (disabled, focussed, selected etc) of this TextView.
#### return value
    void
## Examples (display hint messages)

Result:

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/6dca3098-1624-4069-92ab-cf5f5921b643)

Example of full code:

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
        textView1.setHintTextColor(ContextCompat.getColor(this,R.color.orange));

        layout.addView(textView1);
        my_root.addView(layout);
    }


## ref
From Android Official Docs.

https://developer.android.com/reference/android/widget/TextView#setHintTextColor(android.content.res.ColorStateList)
    
    
