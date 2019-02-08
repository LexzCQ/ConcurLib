# ConcurLib
Android concurrency code invocation library 

This library is made to simplify invocation of code in different threads.

Usage examples:

###### For heave threads

```
 DefaultExecutorSupplier.getInstance().forBackgroundTasks().execute(new Runnable() {
            @Override
            public void run() {
                //your code would be run in parallel thread here
            }
        });
```

###### For light threads

```
 DefaultExecutorSupplier.getInstance().forLightWeightBackgroundTasks().execute(new Runnable() {
            @Override
            public void run() {
                //your code would be run in parallel thread here
            }
        });
```
###### For main (UI) thread
```
 DefaultExecutorSupplier.getInstance().forMainThreadTasks().execute(new Runnable() {
            @Override
            public void run() {
                //your code would be run in main (UI) thread here
            }
        });
```

**If you get `CalledFromWrongThreadException` then you probably trying to access view's field from wrong thread.
As solution you can use new code:**
```
runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                       someView.someMethod(someValue);
                    }
                });

```

**or**

```
DefaultExecutorSupplier.getInstance().forMainThreadTasks().execute(new Runnable() {
                    @Override
                    public void run() {
                        someView.someMethod(someValue);
                    }
                });
```


