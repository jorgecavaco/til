# Gradle Cheat Sheet


For a Java project using Gradle 3.4+, then it depends on whether you are build an application or a library.

* For a *library project* or a *library module* in a multiple module project, it is recommended to use the Java-library plugin, so in build.gradle use this ```apply plugin: 'java-library'``` instead of ```apply plugin: 'java'```

* Use either implementation or api, depending on whether you want to expose the dependency to consumers of the library.

### Properties

* The -P flag is for gradle properties
* The -D flag is for JVM properties.
  - The -D argument passed to gradle will not be propagated to the test.
  - You can use the systemProperty in your test block as you have done but base it on the incoming gradle property by passing it with it -P:
    - ```test { systemProperty "cassandra.ip", project.getProperty("cassandra.ip")}```
  - or alternatively, if you are passing it in via -D
    - ```test { systemProperty "cassandra.ip", System.getProperty("cassandra.ip")}```

### List all tasks

$ ./gradlew tasks --all

### List tasks from the master project

$ ./gradlew -q :tasks --all

---
resources

https://docs.gradle.org/current/userguide/java_library_plugin.html
