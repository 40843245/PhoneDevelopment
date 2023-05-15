# setLineSpacing -- Set spacing between each lines.
## intro
It sets spacing between each lines.

Each line other than the last line will have its height multiplied by mult and have add added to it.

## syntax
    setLineSpacing (float add, 
                  float mult)

## parameter 
      add : It determines the number of line spacing.
      mult : It also determines the number of line spacing.
      
      For more details, see the above discussion.
 ## return value
    void
    
 ## Examples
 
 Result:

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/140baf74-3786-4df2-9c2b-1420285b960e)

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
            Spannable word3=new SpannableString(getResources().getString(R.string.word3));
            word1.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.lightGreen)),0,word1.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);

            word2.setSpan(new ForegroundColorSpan(ContextCompat.getColor(this,R.color.orange)),0,word2.length(),Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);

            textView1.setHorizontallyScrolling(false);

            textView1.setText(word1);

            textView1.append("\n");

            textView1.append(word2);

            textView1.append("\n");

            textView1.append(word3);

            textView1.append("\n");

            textView1.setLineSpacing(1,4);

            layout.addView(textView1);
            my_root.addView(layout);
        }
 
## ref
From Android Official Docs.

https://developer.android.com/reference/android/widget/TextView#setLineSpacing(float,%20float)
