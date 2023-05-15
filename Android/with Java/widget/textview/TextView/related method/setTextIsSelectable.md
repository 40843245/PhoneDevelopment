# setTextIsSelectable -- Determine the text in TextView is selectable.
## intro
It determine the text in TextView is selectable.

When NOT invoked, the property textIsSelectable defaults to false which causes the text is NOT selectable.

You can also change it by setting an XML attribute R.styleable.TextView_textIsSelectable. 

## syntax
      setTextIsSelectable (boolean selectable)
## parameter
      selectable : a bool value that indicates the text is selectable.
      
      When false, the text is NOT selectable.
      
      When true, the text is selectable. 
      
      When the Text is selectable, you can select it and copy it as same as the behavior of selection of a text in other webpage.
Result:
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/1d6210f3-a0a6-4ece-a4f1-a8a0b3b9819b)

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
https://developer.android.com/reference/android/widget/TextView#setTextIsSelectable(boolean)
