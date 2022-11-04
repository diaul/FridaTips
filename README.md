# FridaTips
Random tips because I have bad memory.

# Reading jstring with Frida
When debugging JNI sometimes is useful to read the jstring parameter pass to a functions

```
onEnter(log, args, state) {
  log('Java_com_diaul_my_jni_etc_Etc()');
  var ptr_my_var = args[2];
  Java.perform( function () {
    var String = Java.use("java.lang.String");
    var my_var = Java.cast(ptr(ptr_my_var), String);
    log(my_var);
  });
},
```
