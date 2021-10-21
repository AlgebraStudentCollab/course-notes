## Double checked locking
Most correct solution
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

```java
public static Elvis getInstance() {
        synchronized (Elvis.class) {
            if (instance == null) {
                instance = new Elvis();
            }
        }
        return instance;
    }
```