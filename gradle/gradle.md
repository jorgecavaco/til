# Gradle Cheat Sheet


For a Java project using Gradle 3.4+, then it depends on whether you are build an application or a library.

* For a *library project* or a *library module* in a multiple module project, it is recommended to use the Java-library plugin, so in build.gradle use this ```apply plugin: 'java-library'``` instead of ```apply plugin: 'java'```

* Use either implementation or api, depending on whether you want to expose the dependency to consumers of the library.


---
resources

https://docs.gradle.org/current/userguide/java_library_plugin.html
