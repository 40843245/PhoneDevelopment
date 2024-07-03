# common issue of error in Android Studio
## Q1: Solve the error message.
> Could not set unknown property 'classifier' for task ':line-sdk:sourcesJar' of type org.gradle.api.tasks.bundling.Jar.
## A1:
Above Gradle 8, the 'classifier' is obsolete. Use 'archiveClassifier' instead

## Ref
From stackoverflow,

https://stackoverflow.com/questions/75660848/could-not-set-unknown-property-classifier-for-task-idl-parsersourcejar-of
