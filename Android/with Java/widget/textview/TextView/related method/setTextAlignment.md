# setTextAlignment -- Set the alignment of text.
## intro
It sets the alignment of text.
## syntax
    setTextAlignment (int textAlignment)
    
## parameter
    textAlignment : It should be one of these
    
    TEXT_ALIGNMENT_INHERIT, 
    TEXT_ALIGNMENT_GRAVITY, 
    TEXT_ALIGNMENT_CENTER, 
    TEXT_ALIGNMENT_TEXT_START, 
    TEXT_ALIGNMENT_TEXT_END, 
    TEXT_ALIGNMENT_VIEW_START, 
    TEXT_ALIGNMENT_VIEW_END
    
    Notice that the constants are defined in View class.
    
## return value
    void
## Examples

Result:
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/e8a0d96b-26ff-496b-9892-e97075ee88ce)


Example of full code.

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

            //textView1.setLineSpacing(1,4);
            textView1.setTextAlignment(View.TEXT_ALIGNMENT_CENTER);
            textView1.setJustificationMode(LineBreaker.JUSTIFICATION_MODE_INTER_WORD);
            layout.addView(textView1);
            my_root.addView(layout);
        }

## ref
https://developer.android.com/reference/android/view/View#setTextAlignment(int)
