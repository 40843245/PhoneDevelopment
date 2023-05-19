# Calculate elapse time from running a project
## Objectives
As the title says, in this article, I will teach you, in Android Studio, how to calculate the elapse time from start of a project to now. 

Then update it.

## Prequisite 
1. Basic concept of elapse time.
2. Basic concept of an event handler.
## Review
If you dont know about the prequisites, dont worry. It is simpler than understanding concept of OOP. 

Additionally, I will use the as simple as I can way to introduce them.

Let's get started.

1. elapse time : 
 
Elapse time from start of a project to now refers the difference between now and start of a project.

It can simply be represented as the formula.

 elapse time from start of a project to now = now - start of a project.

2. event handler : 

Consider the following scenario.

Once specified conditions are both met (or 1 condition is met), then immediately invoke the event handler.

### NOTICE 
Notice that there are difference between event handlers and event callback functions.

However, event handlers are 1 kind of event callback functions.

For more details, see the reply StackOverflow.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/7be77ee7-3cb4-4984-a748-012d5d14f78e)

https://stackoverflow.com/questions/2069763/difference-between-event-handlers-and-callbacks


## HOW TO
To do the task mentioned in Objectives section, simply use the event handler for updating and System.currentTimeMillis to get the elapse time from epoch time to now. I describe them in these following steps.

1. Set the variable startTime as System.currentTimeMillis() before performing any operations.
2. Write your code in event handler.
3. Postpone to call the event handler by postDelayed method such as 
    
       timerHandler.postDelayed(this, 500);
       
4. Dont forget to postpone the call of the same event handler after execution the event handler. 

For more details, see the following example.
## Example
### Piece of code.

        TextView timerTextView;
        long startTime;
        Handler timerHandler = new Handler();


        Runnable timerRunnable;

        startTime=System.currentTimeMillis() ;

        timerTextView=(TextView) findViewById(R.id.TextView_1);

        timerTextView.setTextSize(25f);


        timerRunnable= new Runnable()
        {

            @Override
            public void run()
            {

                long millis = System.currentTimeMillis() - startTime;
                int seconds = (int) (millis / 1000);
                int minutes = seconds / 60;
                seconds = seconds % 60;

                timerTextView.setText("");
                timerTextView.append("The project running elapse time\n which determined by \nthe System.currentTimeMillis():");
                timerTextView.append("\n");
                timerTextView.append(String.format("%d:%02d", minutes, seconds));

                timerHandler.postDelayed(this, 500);
            }
        };

        timerHandler.postDelayed(timerRunnable,500);
      
### Explan to the piece of code
1. The variable startTime records the time of start of the project.

2. The variable timerRunnable is a Runnable interface so that it can execute the event handler once after it scheduled.

3. The event handler of timerRunnable is initialized in the constructor of the interface Runnable.
4. The event handler of timerRunnable is run()
5. The last statment of the piece of code 
      
       timerHandler.postDelayed(timerRunnable,500);
       
tell us that the task about timerRunnable is scheduled after 500 ms of start of the project. (i.e. after 500 ms of start of the project the event handler of timerRunnable will be invoked.)

6. The last statement of declaration of timerRunnable

       timerHandler.postDelayed(this, 500);
       
tell us that the task about timerRunnable is scheduled after 500 ms of the task complete to execute (i.e. after 500 ms of start of the project the 
event handler of timerRunnable will be invoked.) so that the event handler of timerRunnable will be able to be invoked forever.

Since it does NOT automatically schedule the task after completion, you have to reschedule it after completion. Although, it may not be convenient to use, it is more flexible to perform different operations and to schedule the task.

The concept of this is same as reset the counter after completion of tasks.

## Ref

Thanks this reply on StackOverflow, it offers an ideas and saves me lots of time.

![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/25ec7c9a-16d1-4f63-ab4c-01b3ed964f14)


https://stackoverflow.com/questions/4597690/how-to-set-timer-in-android

About event handler:

https://stackoverflow.com/questions/2069763/difference-between-event-handlers-and-callbacks








