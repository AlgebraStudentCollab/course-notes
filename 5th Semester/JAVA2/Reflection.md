# Java reflection basics

## Class
Storing a class in a `Class` object
```java
Class c = Class.forName(classname);
```

The `forName()` method requires the class' fully qualified name (eg. `hr.algebra.Main`)

## Fields
Accessing a class' fields via the `Class` object
```java
Field[] publicFields = c.getFields();
Field[] allFields = c.getDeclaredFields();
```

The method `getFields()` returns only public fields,
while `getDeclaredFields()` method returns _all_ fields declared in the class.

## Modifiers
```java
(Fiield)