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

