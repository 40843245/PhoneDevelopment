## syntax

    setTextSize (float size)
    
    setTextSize (int unit, 
                float size)
             
### parameter
    unit : dimension units. For possible dimension units, see TypedValue class.
    size : The size of the text in TextView.
    
### return value
    void
## NOTICE
Notice that
        
        If this TextView has the auto-size feature enabled, then this function takes no effects.


## Example
Result:
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/53c30bcc-95ee-44df-b0d5-9891938172bf)


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

            textView1.setTextIsSelectable(true);

            textView1.setTextSize(18.4f);

            textView1.setHorizontallyScrolling(false);

            textView1.setText(word1);

            textView1.append("\n");

            textView1.append(word2);

            textView1.append("\n");

            textView1.append(word3);

            textView1.append("\n");

            //textView1.setLineSpacing(1,4);
            textView1.setTextAlignment(View.TEXT_ALIGNMENT_CENTER);
            textView1.setJustificationMode(LineBreaker.JUSTIFICATION_MODE_INTER_WORD);
            layout.addView(textView1);
            my_root.addView(layout);
        }
 ## ref
 https://developer.android.com/reference/android/widget/TextView#setTextSize(int,%20float)
