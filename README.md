# learningdart

This project is my "learningdart" repo based off
Chapter 3 - Introduction to Dart from:
[37 hour flutter course](https://www.youtube.com/watch?v=VPvVD8t02U8)
See: 
* (01:14:42) Introduction to Dart
* (02:01:26) Dart Control Statements and Collections
* (02:46:44) Sound Null safety in Dart
* (03:27:12) Dart Enumerations, Classes and Objects
* (04:18:36) Advanced Dart

Included in the dart code for this program are:

* keywords, reserved words
* data types, see [A tour of the Dart language](https://dart.dev/guides/language/language-tour)
* constants (const, Const variables are implicitly final, compile-time constant)
* variables
* final (can only be set once)
* functions
* function arguments/parameters
* curly brackets for function body
* formatting strings
* Dart string formatting
* function shorthand in Dart, =>, instead of using curly brackets.

This repo also includes examples of concepts introduced in
[Chapter 4 - Dart control statements and collections](https://www.youtube.com/watch?v=VPvVD8t02U8&t=7286s)

## Chapter 4:  Dart control statements and collections

* conditionals in Dart
* if... else...
* if... else... if...
* operators:  +,-,*, and /
* discussed prefix operators, infix operators, and suffix operators
* can also create custom operators in classes.  
* Lists
  * like arrays in other langs, like Java and C#) e.g. `['Foo', 'Bar', 'Baz']`
  * List are 0 based indexes, like other langs
  * uses square brackets, e.g. `[]`
  * List can be fixed or growable see [List&lt;E&gt; class](https://api.dart.dev/stable/2.17.6/dart-core/List-class.html)
* Sets
  * List has a single, homogeneous type for each thing.  A set has a unique type for each thing in the set.
  * Set uses curly brackets, e.g. `{}`
  * a Set ensures its data isn't duplicated, e.g. `var names = {'foo', 'bar', 'baz'}; names.add('foo'); print(names); //still only prints 'foo, bar, baz'`
  * Dart will make a set all of the same type, if all elements/things/objects are the same type.
  * However, Dart will make it `Object` if heterogeneous types, e.g. `var names = {'foo', 1};`
* Maps
  * a key-value pair of information
  * e.g. `final Map<int, String> aMapOfIntsAndsStrings = {0: "Red", 1: "Blue" , 2: "Yellow"};`
  * like a dictionary in other langs
  * also like JSON
  * each Key must be unique
  * Dart infers the type for key and value, and it cannot be violated later w/out an error

## Chapter 5:   Sound Null-safety in Dart

* In Dart 2.0, types are null safe by default, but can be made null. e.g. `int?`
* see [Sound null safety](https://dart.dev/null-safety) and [Understanding null safety](https://dart.dev/null-safety/understanding-null-safety)
* at second link, check out `Never` datatype.  Unique to Dart?
* Also went over cherry-picking non-null values with the `??` operator.
* `??=` is the null aware assignment operator.  It will only assign the value from the right, if the operand on the left is null.
* `?.` conditionally invoke the member IF member is not null.

Notes:
There is a convention in Dart that your code should be in camel case per [Vandad](https://www.youtube.com/c/vandadnp).
Dart can make a string using single or double quotes, like JavaScript.
After saving code, Ctrl + S in Windows, the code is hot reloaded, and updated code is run.  
String formatting in Dart, e.g. '$firstName $lastName' is like string interpolation in C#.
Note in Dart, curly brackets are preferred instead of using => shorthand.

## Chapter 6 - Dart enumerations, classes and objects

* enumerations are named lists of enumerated items
* create using reserve word `enum` like other programming langs
* instead of using camel case, use upper case for the first letter of all words, e.g. `PersonPlaceOrThing`
* can refer to using the dot notation, e.g. `enum PersonProperties { firstName, lastName, ... } ... PersonProperties.firstName.name //prints out name`, again like C# and other langs
* Vandad then explains `return` and `break`.  They function like other programming langs.
* Classes
  * uses encapsulation (OOP concept) to put methods and properties in the same object, just like Java, C#, etc.
  * upper case the first letter of every word, e.g. `class Employee...`
  * Vandad covered instances and object. e.g. `final myPerson = new Person();`
* Object
  * instance of a class
* constructors
  * special logic that builds the object or class.  (Just like Java and C#)
  * also called initializers
  * constructor setup is different than C#
    * C# example:

```c#
public class Person
{
   private string last;
   private string first;

   public Person(string lastName, string firstName)
   {
      last = lastName;
      first = firstName;
   }

   // Remaining implementation of Person class.
}
```

  * Dart example:

```Dart
class Person {
  String firstName;
  String lastName;

  //constructor example:
  Person(this.firstName, this.lastName);

  void wakeUp() {
    return;
  }

  void goToSleep() {}

  void eat() {}

  //printName() returns a string concat of the first and last name.
  String printName() {
    return '$firstName $lastName';
  }

}
```

* methods
  * a function on the class, e.g. `main()`

## Chapter 7 - Advanced Dart

Extensions
Can add an extension to a class using, e.g. on Person class:

```Dart
extension FullName on Persion {
  String get fullName => '$firstName $lastName';
}
```

Future
Futures are data to be returned in the fututer. Uses asych programming. 

e.g. 
```Dart
Future<int> heavyFutureThatMultiplesByTwo(int a) {
  return Future.delayed(const Duration(seconds: 3), () => a * 2);
}
```
In order to use/call a Future, must use async and await as in this example:
```Dart
void test() async {
  final result = await heavyFutureThatMultiplesByTwo(10);
  print(result);
}
```

Streams
Streams are an asynchronous "pipe" of data. They may be continuous, like time is a continuous stream. Can periodically or continuously provide values. 

Basic Stream example:
```Dart
Stream<String> getName() {
  return Stream.periodic(const Duration(seconds: 1), (value) {
    return 'Foo';
  });
}
```
calling Stream example:
```Dart
void test() async {
  await for (final value in getName()) {
    print(value);
  }
  print('Steam finished working');
}
```

Generators
A function that returns a list of things but internally calculates that data in a simple way. Generators generate "iterables" marked with sync* and async*. 

Example generator:
```Dart
Iterable<int> getOneTwoThree() sync* {
  yield 1;
  yield 2;
  yield 3;
}
```
An Iterable is like a lazy list that get calculated on the fly. 
Using `async*` returns a stream, using `sync*` returns a List. 

Exmaple of calling a Generator:
```Dart
void test() {
  for (final value in getOneeTwoThree()) {
    print(value);
    if (value == 2) {
      break;
    }
  }
}
```

Generics 
Allows us to avoid writting the same code over and over again. 

Example using generic types `A` and `B`:
```Dart
class Pair<A, B> {
  final A value1;
  final B value2;
  Pair(this.value1, this.value2);
}
```

## Chapter 8 - Project Setup
To go directly to the video for chapter 8, see:
[Chapter 8 - Project Setup](https://www.youtube.com/watch?v=VPvVD8t02U8&t=18041s)


<!--
## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
-->