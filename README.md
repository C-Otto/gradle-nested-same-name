`:aaa` includes both `:bbb` and `:aaa:bbb`, which contain a class with the same name.
The code in `:aaa` calls this class and reports the subproject that was used. 

```
$ ./gradlew run

> Task :aaa:run
:bbb
```