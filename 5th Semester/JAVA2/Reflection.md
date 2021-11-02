# Java reflection basics

Storing a class in a `Class` object
```java
Class c = Class.forName(classname);
```

Accessing a class' fields via the `Class` object
```java
Field[] fields = c.getDeclaredFields();
Field[] fields = c.getFields();
```

