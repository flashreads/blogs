---
id: 014-callbacks-in-java
title: CallBacks in Java
tags:
  - java
  - interface
  - callbacks
  - asynchronus calls
date: 2021-03-01 21:53:39 +0600
keywords: java, callbacks, async
template: post
categories: 
  - java
cover: ../../images/categories/java.png
author: Antar Roy
meta-description: how to use callbacks to perform some tasks after an asynchronus event in java
---

# Using Callbacks to perform some task after an Async event in Java

Let's discuss the problem first and then we can understand what a callback is!

Let's see a code that does some async task which might take some time but we want to do some other work in the meantime. After getting the response or the data been produced, we want to consume the data.

```java
class MyThread extends Thread{
    @Override
    public void run() {
        super.run();
        // some api calls or async task that might take some time
    }
}
public class Main {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        myThread.start();
        // now we dont want to wait, instead we want to initialize the ui with basic components
        initUi();
        // after getting the response from the api, we want to update the ui.
        // but the code won't wait for that to end and waiting is not a option for us
    }
}
```

Now how can we know when the data is ready to consume rather than waiting for it?

Well, that's where Callback comes in. The word `Callback` is self-describing. It is calling back, like instead of going forward, we are going backward! Let's create two concrete methods `onSuccess()` and `onFailure()` and let the thread that is running separately, call these methods back to the main thread! We will create an interface and pass an object to the thread.

```java
interface Callback{
    void onSuccess(Data data); // method that to be called if the task succeded
    void onFailure(Data data); // method that to be called if the task failed
}
class MyThread extends Thread{
    Callback callback;
    MyThread(Callback callback){
        this.callback = callback;
    }
    @Override
    public void run() {
        super.run();
        // some api calls or async task that might take some time
        if(response.status == SUCCESS)callback(response.data);
        else callback(response.errorMessage);
    }
}
public class Main {
    public static void main(String[] args) {
        MyThread myThread = new MyThread(new Callback() { // passing the
            @Override
            public void onSuccess(Data data) {
                loadSuccessUi(data);
            }

            @Override
            public void onFailure(Data data) {
                loadFailureUi(data);
            }
        });
        myThread.start();
        loadUi();
        // now initial ui will be loaded without waiting for the response
        // when the reponse is ready the ui will be updated
    }
}
```

We will give the desired body to onSuccess and onFailure methods and then pass the object to the new thread that will call these methods back to the main thread and pass necessary args.

In short, these two methods are working on the main thread but getting invoked from the seprate thread!
