## Double checked locking
### Most correct solution
Now the instance is marked as [[Volatile|volatile]], meaning that it is always 
```java
private static volatile Elvis instance;

    public static Elvis getInstance() {
        if (instance == null) {
            synchronized (Elvis.class) {
                if (instance == null) {
                    instance = new Elvis();
                }
            }
        }
        return instance;
    }
```

### Almost correct solution
A compromise between thread safety and performance, except if the instance is left in an inopportune state due to a previous thread
```java
private static Elvis instance;

    public static Elvis getInstance() {
        if (instance == null) {
            synchronized (Elvis.class) {
                if (instance == null) {
                    instance = new Elvis();
                }
            }
        }
        return instance;
    }
```

### Slow thread safety
Thread safety is achieved, but now every request for the instance is much slower
```java
private static Elvis instance;

    public static Elvis getInstance() {
	    synchronized (Elvis.class) {
            if (instance == null) {
               instance = new Elvis();   
            }
        }
        return instance;
    }
```

### Bad thread safety
Multiple threads can get in througgh the first if and request an instance sequentially
```java
private static Elvis instance;

    public static Elvis getInstance() {
        if (instance == null) {
            synchronized (Elvis.class) {
                instance = new Elvis();
            }
        }
        return instance;
    }
```

No thread safety
```java
public static Elvis getInstance() {
        if (instance == null) {
            instance = new Elvis();
        }
        return instance;
    }
```