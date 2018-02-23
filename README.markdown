# The Official  XxxXxxxx  Swift Style Guide

## Introduction

Our guide is a collection of general rules. We have collected these rules to unify and maintain the clarity of the code, written by various developers in our company.

## Table of Contents

* [Naming And Syntax](#naming-and-syntax)
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

## Naming And Syntax

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

Use compiler inferred context to write shorter, clear code.

**Preferred:**
```swift
let selector = #selector(viewDidLoad)
view.backgroundColor = .red
let toView = context.view(forKey: .to)
let view = UIView(frame: .zero)
```

**Not Preferred:**
```swift
let selector = #selector(ViewController.viewDidLoad)
view.backgroundColor = UIColor.red
let toView = context.view(forKey: UITransitionContextViewKey.to)
let view = UIView(frame: CGRect.zero)
```

For empty arrays and dictionaries, use type annotation.

**Preferred:**
```swift
var names: [String] = []
var lookup: [String: Int] = [:]
```

**Not Preferred:**
```swift
var names = [String]()
var lookup = [String: Int]()
```

Prefer compact code and let the compiler infer the type for constants or variables of single instances. Type inference is also appropriate for small (non-empty) arrays and dictionaries. When required, specify the specific type such as CGFloat or Int16.

**Preferred:**
```swift
let message = "awsome"
let currentBounds = computeViewBounds()
let distance = 5.5 // of course it's Double
let viewHeight: CGFloat = 200.0
let score = -5  // of course it's Int
let rowNumber: UInt = 7
var names = ["Mic", "Sam", "Christine"]
```

**Not Preferred:**
```swift
let message: String = "awsome"
let currentBounds: CGRect = computeViewBounds()
let distance: Double = 5.5
let score: Int = -5
```

When creating custom delegate methods, an unnamed first parameter should be the delegate source. (UIKit contains numerous examples of this.)

**Preferred:**
```swift
func rangeSlider(_ rangeSlider: RangeSlider, didChangeRange range: (Int, Int))
```

**Not Preferred:**
```swift
func didChangeRange(rangeSlider: RangeSlider, range: (Int, Int))
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

### Final

Marking classes or members as final in tutorials can distract from the main topic and is not required. Nevertheless, use of final can sometimes clarify your intent and is worth the cost. In the below example, Box has a particular purpose and customization in a derived class is not intended. Marking it final makes that clear.

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

When they are needed, use comments to explain why a particular piece of code does something. Comments must be kept up-to-date or deleted.

Avoid block comments inline with code, as the code should be as self-documenting as possible. Exception: This does not apply to those comments used to generate documentation.

*[Table of Contents](#table-of-contents)

## Documentation

*[Table of Contents](#table-of-contents)

