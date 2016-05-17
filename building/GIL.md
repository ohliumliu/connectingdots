#Global interpreter lock

[Wiki](https://en.wikipedia.org/wiki/Global_interpreter_lock)

In scripting languages, the interpreter can only process one thread at a time for thread safety. For example, CPython (C implementatio
of Python) and Ruby MRI (C implementation of Ruby) use GIL. It is necessary because the underlying C code is not thread safe. The downside
is the limitation of parallelism.
