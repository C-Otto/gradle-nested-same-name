Build fails due to duplicate subproject name. Renaming `:bbb` to `:bbb2` fixes this. 

```
$ ./gradlew build
FAILURE: Build failed with an exception.

* What went wrong:
Circular dependency between the following tasks:
:aaa:bbb:classes
\--- :aaa:bbb:compileJava
     \--- :aaa:bbb:jar
          \--- :aaa:bbb:classes (*)

(*) - details omitted (listed previously)


* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 690ms
```

```
$ ./gradlew aaa:bbb:dependencies --configuration compileClasspath

> Task :aaa:bbb:dependencies

------------------------------------------------------------
Project ':aaa:bbb'
------------------------------------------------------------

compileClasspath - Compile classpath for source set 'main'.
+--- project :aaa
\--- project :bbb -> project :aaa:bbb (*)

(*) - dependencies omitted (listed previously)

A web-based, searchable dependency report is available by adding the --scan option.

BUILD SUCCESSFUL in 651ms
1 actionable task: 1 executed
```