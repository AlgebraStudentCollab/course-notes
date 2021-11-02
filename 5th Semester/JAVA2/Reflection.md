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

Field field = allFields[0];
```

The method `getFields()` returns only public fields,
while `getDeclaredFields()` method returns _all_ fields declared in the class.

## Modifiers
```java
int modifier = field.getModifiers();
```

`getModifiers()` returns a binary encoded list of modifiers. They can easily be parsed with the `Modifier` class.

```java
Modifier.isFinal(modifier);
Modifier.isPublic(modifier);
Modifier.isProtected(modifier);
Modifier.isPrivate(modifier);
...
```

The `Modifier` class has several static helper methods which return Booelan values representing the specified modifier.