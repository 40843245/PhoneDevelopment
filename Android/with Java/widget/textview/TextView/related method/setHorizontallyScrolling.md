# setHorizontallyScrolling -- Set the text should be wider than the width of the TextView.
## intro
In the method setHorizontallyScrolling(bool whether),

it sets the text should be wider than the width of the TextView (if needed).

Only when the text is wider than the width of the TextView, the method takes effects.

Case 1 : When the text is wider than the width of the TextView and if whether is set to true,

          then the text will be overflow the TextView (i.e. it will NOT be wrapped.).
          
Case 2 : When the text is wider than the width of the TextView and if whether is set to false,

          then the text will be wrapped. (i.e. the rest of the text will display in the next line.)
          
## syntax
    setHorizontallyScrolling(bool whether)
## parameter 
    whether : a bool value that indicates the text should NOT be wrapped (if needed.)
## return value 
    void
    
## Resources for examples
I define them in .../res/values/strings.xml as follows.

    <resources>
      <string name="app_name">BuiltinFilePicker_Project_1</string>
      <string name="word1">Word1</string>
      <string name="word2">Word2</string>
      <string name="word3">A very,very,very,very,very,very,very,very,very,very,very,very,very,very long texts.</string>
    </resources>

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/75d2b41a-dcc2-4a0f-8d05-7192dc5ebfca)


## Example (parameter whether == false)
Result:

  ![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/32449993-df16-488d-bad6-fe87f1152e11)

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



        layout.addView(textView1);
        my_root.addView(layout);
    }
  
## Example (parameter whether == true)

Result:

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/f8814122-3119-48f7-9234-ea7abb60f9c4)


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

        textView1.setHorizontallyScrolling(true);

        textView1.setText(word1);

        textView1.append("\n");

        textView1.append(word2);

        textView1.append("\n");

        textView1.append(word3);

        textView1.append("\n");



        layout.addView(textView1);
        my_root.addView(layout);
    }

## ref
From Android Official Docs.

https://developer.android.com/reference/android/widget/TextView#setHorizontallyScrolling(boolean)


