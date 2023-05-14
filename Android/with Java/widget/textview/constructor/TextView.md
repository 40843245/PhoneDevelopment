# TextView -- A view that display text.
## Objectives
In this article, I will discuss all details about TextView class.
  
    What is TextView class in Android Studio?
    
    Usage and instantiation of TextView. 
    
    Notices about TextView. (You must pay lots of attention. Otherwise, you may stick on bugs for a long time. I have stuck on them.)
    
    More learning references.
    
## Intro 

The TextView class is a class that handles a view to display text.

That is to say, to display a text or texts, the TextView class must be used.

##  Usage and instantiation of TextView. 

Instantiate it with new keyword. Then append it into a Layout instance. Finally, append the view into the root layout.

## Exampple

See the following example.

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

        //TextView textView1= (TextView) findViewById(R.id.text_view_id_1);
        TextView textView1 = new TextView(this);
        textView1.setTextColor(ContextCompat.getColor(this, R.color.orange));
        textView1.setText("ANDROID APP");
        //textView1.setHeight(4);
        layout.addView(textView1);
        my_root.addView(layout);
        
        }

## NOTICES

Again, I want to remind you that you must pay lots of attention. Otherwise, you may stick on bugs for a long time. I have stuck on them.
    
    
1. There can be at least 1 TextView in a root layout. Otherwise, the bug occurs when running. (NO compiler error but it will cause the application on Android device can NOT be executed.)

More details on the replies on StackOverflow.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/125aed3c-21bd-4877-ae6c-f09d555f040d)

https://stackoverflow.com/questions/38967510/two-textview-next-to-each-other

## Ref

Replies on StackOverflow.

https://stackoverflow.com/questions/38967510/two-textview-next-to-each-other


