---
id: 009-difference-between-finally-finalize.md
title: Java Final vs Finally vs Finalize
tags: java, final, finally, finalize, comparison
author: Daita Sur
meta-description: Learn the difference between keywords final, finally and finalize in Java.
---

# Java Final vs Finally vs Finalize

This is a very common question which one might face in an interview. So today we are going to discuss the three keywords final, finally, and finalize which are frequently confused. First, let me tell you what a keyword is. A keyword is a reserved word which has a predefined meaning in the language. Because of this, you cannot use keywords as names for variables, methods, classes, or any other identifiers. There are 51 keywords in Java.
So now you know what a keyword is, let us see the differences between the keywords final, finally, and finalize.

## Final Keyword

Final is a keyword used to apply restriction on class, method, and variable. So, a final class cannot be inherited, a final method cannot be overridden, and a final variable cannot be changed. A final variable that has no value is called blank final variable or uninitialized final variable.

```java
final String your_name;
```
Below is an example of a final variable

```java
class FinalExample
{
    public static void main()
    {
        final int a=10;
        a=5;  //compile Time error
    }
}
```

So what is going on?

a=5 shows a compile time because once a variable is declared you cannot change its value.

Also, you should know that a final variable is inherited. So, you cannot declare a constructor as final because a constructor is not inherited.

## Finally keyword

Finally is a block used in try-catch. Each try contains one and only one finally block. It will be executed whether an exception is handled or not.

```java
class FinallyExample
{
    public static void main()
    {
        try
        {
            int a=25;
            System.out.println(a);
        }
        catch(Exception e)
        {
            System.out.println(e);
        }
        finally
        {
            System.out.println("finally block is always executed");
        }
    }
}
```
OUTPUT:
25
finally block is always executed

## Finalize keyword

Finalize is a method used to perform clean up processing just before the object is garbage collected. Before the object is garbage collected, the runtime system calls its finalize() method.

```java
public class FinalizeExample 
{  
     public static void main(String[] args)   
    {   
        FinalizeExample obj = new FinalizeExample();   
        obj = null;   
        // calling garbage collector    
        System.gc();   
        System.out.println("end of garbage collection");   
  
    }   
    @Override 
    protected void finalize()   
    {   
        System.out.println("finalize method called");   
    }   
} 
```
OUTPUT:
end of garbage collection
finalize method called

So, in a nutshell the differencve between final, finally, and finalize is final is a keyword, finally is a block and finalize in a method.

Thanks!!
