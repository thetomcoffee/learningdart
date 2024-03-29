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
  * like arrays in other langs like Java and C#), e.g. `['Foo', 'Bar', 'Baz']`
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
  * like a dictionary in other langs
  * also like JSON
  * each Key must be unique
  * Dart infers the type for key and value, and it cannot be violated later w/out an error

## Chapter 5:   Sound Null-safety in Dart

* In Dart 2.0, types are null safe by default, but can be make null.
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