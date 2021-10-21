### Enum solution


### Most correct solution with a class
Now the instance is marked as [[Volatile|volatile]], meaning that any changes to the instance are shared between threads.
```java
public class Elvis implements Serializable {
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
The [[Synchronized|synchronized]] expression stops multiple threads from accessing a section of code simoultaneously.
Multiple threads can get in through the first if and request an instance sequentially.
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