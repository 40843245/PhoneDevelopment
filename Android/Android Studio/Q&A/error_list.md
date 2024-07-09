# common issue of error in Android Studio
## Q1: Solve the error message.
> Could not set unknown property 'classifier' for task ':line-sdk:sourcesJar' of type org.gradle.api.tasks.bundling.Jar.
## A1:
Above Gradle 8, the 'classifier' is obsolete. Use 'archiveClassifier' instead

## Ref
From stackoverflow,

https://stackoverflow.com/questions/75660848/could-not-set-unknown-property-classifier-for-task-idl-parsersourcejar-of

## Q2: How to solve internal error about Android studio?
Such as 

Internal error. Please refer to https://issuetracker.google.com/issues/new?component=192708  

java.lang.RuntimeException: Could not find installation home path. Please make sure bin/idea.properties is present in the installation directory.     at com.i

## A2:
It looks like you have a corrupted installation file.

Thus, completely uninstall Android Studio and download it again from the website.

## Ref
https://stackoverflow.com/questions/31733548/internal-error-please-report-to-https-code-google-com-p-android-issues

## Q3: Solve the error message.
The application could not be installed.

## A3:
There are many reasons to cause this error.

The most reason is that invalid data in cache. To solve it, please clear the data in cache. Follow these steps:

1. In Android Studio, on top left of window, Navigate File -> Invalidate Caches/Restart.
2. I highly recommend to tick all checkbox in popup.
3. Click "OK" button.
   
## Ref
https://stackoverflow.com/questions/58829786/android-studio-the-application-could-not-be-installed-shell-unresponsive#:~:text=The%20solution%20is%20to%20download%20the%20appropriate%20pack,the%20version%20for%20Android%20and%20choose%20all%20packages.
