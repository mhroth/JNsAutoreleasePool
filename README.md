# JNsAutoreleasePool

Holy crap, is this a specialised piece of code. Suppose you have a Java project with JNI components. Suppose those JNI components interact with libraries written in Objective-C. Suppose further that those ObjC libraries assume that their parents will handle basic infrastructure such as `NSAutoreleasePool`s, etc. But the parents don't provide this infrastructure because they aren't ObjC libraries themselves. Perhaps they were written in C or C++. And they are interfacing with normal C-like functions in your Objective-C code.

So you need a way to add this infrastructure so that you don't get memory leaks. Enter `JNsAutoreleasePool`. Put this object at the beginning of a Java thread which will interact with ObjC code, and move on with life.