# The Official  XxxXxxxx  Swift Style Guide

## Introduction

Our guide is a collection of general rules. We have collected these rules to unify and maintain the clarity of the code, written by various developers in our company.

## Table of Contents

* [Naming](#naming)
* [Code Formatting](#code-formatting)
* [Code Organization](#code-organization)
* [Classes and Structures](#classes-and-structures)
* [Function Declarations](#function-declarations)
* [Closure Expressions](#closure-expressions)
* [Computed Properties](#computed-properties)
* [Statements](#statements)
* [Control Flow](#control-flow)
* [Types](#types)
* [Comments](#comments)
* [Documentation](#documentation)

## Naming

Use UpperCamelCase for types and protocols.
```swift
protocol SomeProtocol { /* ... */ }

class SomeClass: SomeProtocol { /* ... */ }

struct SomeStruct { /* ... */ }

enum DaysOfTheWeek { /* ... */ }

typealias GridPoint = (Int, Int)
```

Use camelCase for instances, variables, constants and everything else.
```swift
let someObject = SomeClass()

var x = 0

var firstDay: DaysOfTheWeek = .monday
```

Names should be descriptive and unambiguous.
Do not abbreviate, use shortened names, or single letter names.


**Preferred:**
```swift
class StarShapeLabel: UILabel { /* ... */ }

var resultOfDiceRoll: Int {
    // roll of dice
    return 3 // I promise, it was fair dice roll ...
}

let animationDuration: NSTimeInterval
```

**Not Preferred:**
```swift
class CustomLabel: UILabel { /* ... */ }

var randomNumber: Int {
    // roll of dice
    return 3
}

let aniDur: NSTimeInterval
```

Include type information in constant or variable names when it is not obvious otherwise.
```swift
class ChatUserTableViewCell: UITableViewCell {

    @IBOutlet weak var submitButton: UIButton!
    @IBOutlet weak var emailTextField: UITextField!
    @IBOutlet weak var nameLabel: UILabel!
    @IBOutlet weak var personImageView: UIImageView!

    var personImage: UIImage?

    // it is ok not to include string in the ivar name here because it's obvious
    // that it's a string from the property name
    var firstName: String?
}

// though not preferred, it is OK to use `Controller` instead of `ViewController`
let popupController: UIViewController
let popupViewController: UIViewController

// when working with a subclass of `UIViewController` such as a table view
// controller, collection view controller, split view controller, etc.,
// fully indicate the type in the name.
let popupTableViewController: UITableViewController
```

Use US English spelling to match Apple's API.

**Preferred:**
```swift
let color = "red"

var grayButton: UIButton!

func setBehavior() { /* ... */ }
```

**Not Preferred:**
```swift
let colour = "red"

var greyButton: UIButton!

func setBehaviour() { /* ... */ }
```

When dealing with an acronym or other name that is usually written in all caps, actually use all caps in any names that use this in code. The exception is if this word is at the start of a name that needs to start with lowercase - in this case, use all lowercase for the acronym.
```swift
// "URL" is at the start of a constant name, so we use lowercase "url"
let urlString = "www.applover.pl"
// Prefer using ID to Id
let chatUserID: Int = 13
// Prefer URLFinder to UrlFinder
class URLFinder { /* ... */ }
```

*[Table of Contents](#table-of-contents)

## Code Formatting

### Spacing

Always use 4 space indentations, and remember to select the whole code after finishing the work and press ctrl + i.
It will automatically set all the indents in the right positions.

Method braces and other braces (if/else/switch/while etc.) always open on the same line as the statement but close on a new line.

**Preferred:**
```swift
func myMethod() {
    // body of function
}

if isRainig {
    // take ambrela
} else {
    // you don't need it
}
```

**Not Preferred:**
```swift
func myMethod()
{
// body of function
}

if isRainig {
// take ambrela }
else { // you don't need it }
```

**Exception:**
When You use guard and need just return in case condition fails, open braces on the same line and close on the same line as the statement.
```swift
guard code.isClean else { return }

guard someCondotion else {
    // if you need
    // aditional code here
    return
}
```

Colons always have no space on the left and one space on the right. Exceptions are empty dictionary [:] and #selector syntax for unnamed parameters (_:).

**Preferred:**
```swift
class SomeClass: BaseClass {
    init(data: [String: Int]) {
        self.data = data
    }
    var data: [String: Int] = ["A": 1, "B": 2]
}
```

**Not Preferred:**
```swift
class SomeClass :BaseClass {
    init(data:[String:Int]) {
        self.data = data
    }
    var data : [String : Int] = ["A":1, "B":2]
}
```
### Computed Properties
For conciseness, if a computed property is read-only, omit the get clause. The get clause is required only when a set clause is provided.

**Preferred:**
```swift
var squareArea: Double {
    return sideOfSquare  * sideOfSquare
}
```

**Not Preferred:**
```swift
var squareArea: Double {
    get {
        return sideOfSquare  * sideOfSquare
    }
}
```



*[Table of Contents](#table-of-contents)

## Code Organization

### Minimal Imports

Keep imports minimal. For example, don't import UIKit when importing Foundation will suffice.

### Protocol Conformance
In particular, when adding protocol conformance to a model, prefer adding a separate extension for the protocol methods. This keeps the related methods grouped together with the protocol and can simplify instructions to add a protocol to a class with its associated methods.

**Preferred:**
```swift
class MyViewController: UIViewController {
    // class stuff here
}

// MARK: - UITableViewDataSource
extension MyViewController: UITableViewDataSource {
    // table view data source methods
}

// MARK: - UIScrollViewDelegate
extension MyViewController: UIScrollViewDelegate {
    // scroll view delegate methods
}
```

**Not Preferred:**
```swift
class MyViewController: UIViewController, UITableViewDataSource, UIScrollViewDelegate {
    // all methods
}
```

*[Table of Contents](#table-of-contents)

## Classes and Structures

*[Table of Contents](#table-of-contents)

## Function Declarations

*[Table of Contents](#table-of-contents)

## Closure Expressions

*[Table of Contents](#table-of-contents)

## Computed Properties

*[Table of Contents](#table-of-contents)

## Statements

*[Table of Contents](#table-of-contents)

## Control Flow

*[Table of Contents](#table-of-contents)

## Types

*[Table of Contents](#table-of-contents)

## Comments

*[Table of Contents](#table-of-contents)

## Documentation

*[Table of Contents](#table-of-contents)

