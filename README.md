# learningdart

This project is my "learningdart" repo based off
Chapter 3 - Introduction to Dart from:
[37 hour flutter course](https://www.youtube.com/watch?v=VPvVD8t02U8)

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

* conditionals in Dart
* if... else...
* if... else... if...
* operators:  +,-,*, and /
* discussed prefix operators, infix operators, and suffix operators
* can also create custom operators in classes.  
* List (like arrays in other langs like Java and C#), e.g. `['Foo', 'Bar', 'Baz']`
  * List are 0 based indexes, like other langs
  * uses square brackets, e.g. `[]`
  * List can be fixed or growable see [List&lt;E&gt; class](https://api.dart.dev/stable/2.17.6/dart-core/List-class.html)
* Sets
  * List has a single, homogeneous type for each thing.  Set has a unique type for each thing in the set.
  * Set uses curly brackets, e.g. `{}`
  * a Set ensures its data isn't duplicated, e.g. `var names = {'foo', 'bar', 'baz'}; names.add('foo'); print(names); //still only prints 'foo, bar, baz'`
  * Dart will make a set all of the same type, if all elements/things/objects are the same type.
  * However, Dart will make it `Object` if heterogeneous types, e.g. `var names = {'foo', 1};`

Notes:
There is a convention in Dart that your code should be in camel case per [Vandad](https://www.youtube.com/c/vandadnp).
Dart can make a string using single or double quotes, like JavaScript.
After saving code, Ctrl + S in Windows, the code is hot reloaded, and updated code is run.  
String formatting in Dart, e.g. '$firstName $lastName' is like string interpolation in C#.
Note in Dart, curly brackets are preferred instead of using => shorthand.

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