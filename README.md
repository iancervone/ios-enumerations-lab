# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.



enum IOSDeviceType {
case iPhone (String)
case iPad (String)
case iWatch (Int)

func printDescription() {
switch self {
case .iPhone(let modelType):
print("This is an iphone \(modelType)")
case .iPad(let modelType):
print("This is an iPad \(modelType)")
case .iWatch(let modelType):
print("This is an iWatch \(modelType)")
}
}
}

let myDevice = IOSDeviceType.iWatch(3)
myDevice.printDescription()

let myOtherDevice = IOSDeviceType.iPhone("7+")
myOtherDevice.printDescription()






## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.




enum Shape {
case triangle
case rectangle
case square
case pentagon
case hexagon
}

enum Sides: Int {
case three = 3
case four = 4
case five = 5
case six = 6
}

func numOfSides(shape: Shape) -> Sides.RawValue {
switch shape {
case .triangle: return 3
case .rectangle: return 4
case .square:  return 4
case .pentagon:  return 5
case .hexagon:  return 6    }
}

var myFavoritePolygon = Shape.pentagon
myFavoritePolygon = Shape.hexagon
myFavoritePolygon = Shape.pentagon
myFavoritePolygon = Shape.triangle

var length: Int = 10
func length(shape: Shape) {
print("the perimiter of a \(myFavoritePolygon) is \(((numOfSides(shape: myFavoritePolygon))) * length) feet")
}
print("a \(myFavoritePolygon) has \((numOfSides(shape: myFavoritePolygon))) sides")
length(shape: myFavoritePolygon)





## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.



enum OperatingSystem: String {
case windows = "windows are what i want to throw my computer out of"
case mac = "mac a day keeps the bugs away"
case linux = "linux may be the cousin of the kid with the banket from The Peanuts"
}

var arrayOfSystems = ["windows", "mac", "linux"]

for system in arrayOfSystems {
if system == "windows" {
print(OperatingSystem.windows.rawValue)
} else {
if system == "mac" {
print(OperatingSystem.mac.rawValue)
} else {
if system == "linux" {
print(OperatingSystem.linux.rawValue)
}
}
}
}





## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
```


enum Direction {
case up
case down
case left
case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]


for direction in steps {
print("current location is at x: \(location.x) and at y: \(location.y)")
print("I'm about to go \(direction)")
switch direction {
case . up:
location.y += 1
case . down:
location.y -= 1
case . left:
location.x -= 1
case . right:
location.x += 1
}
}

print("The final location is: \(location)")





## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper


enum HandShape {
case rock
case paper
case scissors
}

enum MatchResult {
case win
case draw
case lose
}


func match(firstShape: HandShape, secondShape: HandShape) -> MatchResult {
switch firstShape {
case .rock:
switch secondShape {
case .rock: return .draw
case .paper: return .lose
case .scissors: return .win
}
case .paper:
switch secondShape {
case .rock: return .win
case .paper: return .draw
case .scissors: return .lose
}
case .scissors:
switch secondShape {
case .rock: return .lose
case .paper: return .win
case .scissors: return .draw
}
}
}
print(match(firstShape: .rock, secondShape: .rock)



## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```



var dollar = 100
enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func oneDollar() -> Int {
switch self {
case .penny: return dollar / CoinType.penny.rawValue
case .nickle: return dollar / CoinType.nickle.rawValue
case .dime: return dollar / CoinType.dime.rawValue
case .quarter: return dollar / CoinType.quarter.rawValue
}
}
}
print(CoinType.dime.oneDollar())

var moneyArray:[(Int,CoinType)] = [(10,.penny),
(15,.nickle),
(3,.quarter),
(20,.penny),
(3,.dime),
(7,.quarter)]
var totalValue = Int()

for value in moneyArray {
if value.1 == CoinType.penny {
totalValue += (value.0 * CoinType.penny.rawValue)
} else {
if value.1 == CoinType.nickle {
totalValue += (value.0 * CoinType.nickle.rawValue)
} else {
if value.1 == CoinType.dime {
totalValue += (value.0 * CoinType.dime.rawValue)
} else {
if value.1 == CoinType.quarter {
totalValue += (value.0 * CoinType.quarter.rawValue)
}
}
}
}
}
print(totalValue)

func oneDollar(coin: CoinType) -> Int {
switch coin {
case .penny: return 100
case .nickle: return 20
case .dime: return 10
case .quarter: return 4

}
}





b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.


## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`



enum DayOfWeek: String {
case sunday = "sunday"
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"

func day() -> [String] {
var matchedDays = [String]()
for days in poorlyFormattedDays {
switch self {
case .sunday:
if DayOfWeek.sunday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .monday:
if DayOfWeek.monday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .tuesday:
if DayOfWeek.tuesday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .wednesday:
if DayOfWeek.wednesday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .thursday:
if DayOfWeek.thursday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .friday:
if DayOfWeek.friday.rawValue == days.lowercased() {
matchedDays += [days]
}
case .saturday:
if DayOfWeek.saturday.rawValue == days.lowercased() {
matchedDays += [days]
}
}
}
return matchedDays
}
}

print(DayOfWeek.monday.day())




c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.



let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]

enum DayOfWeek: String {
case sunday = "sunday"
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"

func isWeekend () -> Int {
var weekDays = [String]()
var weekendDays = [String]()
for days in poorlyFormattedDays {
switch self {
case .monday, .tuesday, .wednesday, .thursday, .friday:
if DayOfWeek.monday.rawValue == days.lowercased() || DayOfWeek.tuesday.rawValue == days.lowercased() || DayOfWeek.wednesday.rawValue == days.lowercased() || DayOfWeek.thursday.rawValue == days.lowercased() || DayOfWeek.friday.rawValue == days.lowercased() {
weekDays += [days]
}
case .sunday, .saturday:
if DayOfWeek.sunday.rawValue == days.lowercased() || DayOfWeek.saturday.rawValue == days.lowercased() {
weekendDays += [days]

}

}
}
return weekDays.count
}
}
DayOfWeek.monday.isWeekend()



## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

c) Write code that prints the train letter or number of your instance of `MetroLine`.



enum MetroLine {
case Green (Int, Int, Int)
case Red (Int, Int, Int)
case Blue (Character, Character, Character)
}
var greenLines = MetroLine.Green(4,5,6)
var redLines = MetroLine.Red(1,2,3)
var blueLines = MetroLine.Blue("a","c","e")

var myLine = redLines

switch myLine {
case .Green(let green1, let green2, let green3):
print("green lines are: \(green1), \(green2), \(green3)")
case .Red(let red1, let red2, let red3):
print("red lines are: \(red1), \(red2), \(red3)")
case .Blue(let blue1, let blue2, let blue3):
print("blue lines are: \(blue1), \(blue2), \(blue3)")
}






## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.
