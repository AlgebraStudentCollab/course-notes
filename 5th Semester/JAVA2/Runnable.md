## Runnable
```java
Runnable runnable = () -> {
	// do something in a thread here
};

ScheduledExecutorService timer = Executors.newSingleThreadScheduledExecutor();
timer.scheduleAtFixedRate(runnable, 0, 100, TimeUnit.MILLISECONDS);
```