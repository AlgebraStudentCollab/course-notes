Android apps | iOS apps
---|---
Run on the Dalvik VM|Compile to native machine code
Android runtime|Objective C runtime

#### quote
_"Its combination of safety and speed make Swift an excellent choice for everything from “Hello, world!” to an entire operating system."_

### Swift

- clarity
- brevity as a side effect
- Names of types and protocols are `UpperCamelCase`. Everything else is `lowerCamelCase`.
- function variable names
- Code written at global scope is used as the entry point for the program, so you don’t need a `main()` function.


### Basic stuff
#### var vs let
```swift
var myVariable = 42
myVariable = 50
let myConstant = 42
```
#### typing
```swift
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
```
#### implicit conversion
```swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
```
#### string interpolation
```swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```
#### arrays and dictionaries
```swift
var shoppingList = ["catfish", "water", "tulips"]
shoppingList[1] = "bottle of water"
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
```
#### for / foreach
```swift
for index in 0..<42 {
	print(index)
}
// Prints from 0 up to and including 41
```
```swift
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
]
var largest = 0
for (_, numbers) in interestingNumbers {
    for number in numbers {
        if number > largest {
            largest = number
        }
    }
}
print(largest)
// Prints "25"
```

#### functions
with external variable names
```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```
without 
```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")

```