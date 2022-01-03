## Runnable
```java
Runnable imageUpdater = () -> {
	// do something in a thread here
};

ScheduledExecutorService timer = Executors.newSingleThreadScheduledExecutor();
timer.scheduleAtFixedRate(imageUpdater, 0, 100, TimeUnit.MILLISECONDS);
```