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

naming
```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```

#### typing
```swift
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
```

optionals and optional unwrapping
```swift
var surveyAnswer: String?

if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}

let possibleNumber: Int? = maybeThisFunctionReturnsAValue()
if let actualNumber = possibleNumber {
	print("\(actualNumber) is here")
} else {
	print("we have been abandoned")
}

if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
// Prints "4 < 42 < 100"

if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            print("\(firstNumber) < \(secondNumber) < 100")
        }
    }
}
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

####  declaring functions
single set of parameter names
```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```
internal and external parameter names
```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")

```

#### tuples
```swift
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    var min = scores[0]
    var max = scores[0]
    var sum = 0

    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        sum += score
    }

    return (min, max, sum)
}
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
print(statistics.sum)
// Prints "120"
print(statistics.2)
// Prints "120"
```

#### fuctions as first class citizens 
as return parameter
```swift
func makeIncrementer() -> ((Int) -> Int) {
	 func addOne(number: Int) -> Int {
		 return 1 + number
	 }
	 return addOne
}
var increment = makeIncrementer()
increment(7)
```
as input parameter
```swift
func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
	 for item in list {
		 if condition(item) {
			 return true
		 }
	 }
	 return false
}

func lessThanTen(number: Int) -> Bool {
	 return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(list: numbers, condition: lessThanTen)
```

#### closures
```swift
let numbers = [20, 19, 12, 7]

let mappedNumbers = numbers.map({ (number: Int) -> Int in
	 let result = 3 * number
	 return result
})
print(mappedNumbers)
  
let mappedNumbers2 = numbers.map({ number in 3 * number })
print(mappedNumbers2)
  
let mappedNumbers3 = numbers.map { number in 3 * number }
print(mappedNumbers3)
  
let mappedNumbers4 = numbers.map { 3 * $0 }
print(mappedNumbers4)

// Prints
// [60, 57, 36, 21]
// [60, 57, 36, 21]
// [60, 57, 36, 21]
// [60, 57, 36, 21]
```

#### objects and classes
```swift
class Shape {
	var numberOfSides = 0
	func simpleDescription() -> String {
		return "A shape with \(numberOfSides) sides."
	}
}

var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```

constructors -> initializers
```swift
class NamedShape {
	var numberOfSides: Int = 0
	var name: String

	init(name: String) {
		self.name = name
	}

	deinit() {
		print("goodbye ~")
	}

	func simpleDescription() -> String {
		return "A shape with \(numberOfSides) sides."
	}
}
```

Every property needs a value assigned—either in its declaration (as with `numberOfSides`) or in the initializer (as with `name`).

override detection @ compile time
```swift
override func simpleDescription() -> String {
	return "A square with sides of length \(sideLength)."
}
```

getters setters
```swift
var sideLength: Double = 0.0

var perimeter: Double {
	get {
		return 3.0 * sideLength
	}
	set {
		sideLength = newValue / 3.0
	}
}
```

on set / after set events
```swift
var triangle: EquilateralTriangle {
	willSet {
		square.sideLength = newValue.sideLength
	}
}
var square: Square {
	willSet {
		triangle.sideLength = newValue.sideLength
	}
}

var name: String {
	didSet {
		print("i just changed my name to \(newValue)")
	}
}
```

#### enumeration
```swift
enum Rank: Int {
	case ace = 1
	case two, three, four, five, six, seven, eight, nine, ten
	case jack, queen, king

	func simpleDescription() -> String {
		switch self {
		case .ace:
			return "ace"
		case .jack:
			return "jack"
		case .queen:
			return "queen"
		case .king:
			return "king"
		default:
			return String(self.rawValue)
		}
	}
}
let ace = Rank.ace
let aceRawValue = ace.rawValue
```

#### structs
always passed by copy
```swift
struct Card {
	var rank: Rank
	var suit: Suit
	func simpleDescription() -> String {
		return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
	}
}
let threeOfSpades = Card(rank: .three, suit: .spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
```

#### protocols & extensions
```swift
protocol ExampleProtocol {
	static var TypeDescription: String { get }
	var simpleDescription: String { get }
	mutating func adjust()
}

class SimpleClass: ExampleProtocol {
    var simpleDescription: String = "A very simple class."
    var anotherProperty: Int = 69105
    func adjust() {
        simpleDescription += "  Now 100% adjusted."
    }
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription

struct SimpleStructure: ExampleProtocol {
    var simpleDescription: String = "A simple structure"
    mutating func adjust() {
        simpleDescription += " (adjusted)"
    }
}
```

errors
```swift
enum PrinterError: Error {
	case outOfPaper
	case noToner
	case onFire
}


func send(job: Int, toPrinter printerName: String) throws -> String {
	if printerName == "Never Has Toner" {
		throw PrinterError.noToner
	}
	return "Job sent"
}

do {
    let printerResponse = try send(job: 1040, toPrinter: "Bi Sheng")
    print(printerResponse)
} catch {
    print(error)
}


do {
    let printerResponse = try send(job: 1440, toPrinter: "Gutenberg")
    print(printerResponse)
} catch PrinterError.onFire {
    print("I'll just put this over here, with the rest of the fire.")
} catch let printerError as PrinterError {
    print("Printer error: \(printerError).")
} catch {
    print(error)
}

let printerFailure = try? send(job: 1885, toPrinter: "Never Has Toner")
```

finally -> defer
```swift
var fridgeIsOpen = false
let fridgeContent = ["milk", "eggs", "leftovers"]

func fridgeContains(_ food: String) -> Bool {
	fridgeIsOpen = true
	defer {
		fridgeIsOpen = false
	}

	let result = fridgeContent.contains(food)
	return result
}
fridgeContains("banana")
print(fridgeIsOpen)
// Prints "false"
```

#### generics
```swift
func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
	var result: [Item] = []
	for _ in 0..<numberOfTimes {
		result.append(item)
	}
	return result
}
makeArray(repeating: "knock", numberOfTimes: 4)
```

requirements
```swift
func anyCommonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> Bool
    where T.Element: Equatable, T.Element == U.Element
{
    for lhsItem in lhs {
        for rhsItem in rhs {
            if lhsItem == rhsItem {
                return true
            }
        }
    }
    return false
}

anyCommonElements([1, 2, 3], [3])
```