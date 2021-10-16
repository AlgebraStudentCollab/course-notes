tags: [[algebra]] [[oop]] 
## Casting Objects in C#
### is
```c#
if(obj is ClassOne)
	...
```
Returns boolean value if the obj instance is the specified class.

### as
```c#
ClassOne classone = obj as ClassOne;
```
Converts instance obj of unknown type to class ClassOne, will result in exception if cannot be cast.

### inline
```c#
if(obj is ClassOne classone)
	...
```
Is equal to the following code:
```c#
if(obj is ClassOne) {
	ClassOne classone = obj as Classone;
	...
```
