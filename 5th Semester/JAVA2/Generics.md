# Generics
Generics offer compile time safety.
# \<T>
T is a standin for whichever type is used in code.
```java
List<String> stringList = new List<>();
```
Typed to `String` explicitly.
# \<?>
? means that the object will be typed, to a class, but isn't defined yet.
An untyped object may accent any object type, while an object typed to ? will only accept objects of the object type defined at initialization.

```java
List<?> stringList = new List<String>();
```
Typed to `String` implicitly.