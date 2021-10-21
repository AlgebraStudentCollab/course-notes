```java

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