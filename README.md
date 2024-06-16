# learningdart

This project is my "learningdart" repo based off:
[Flutter Course for Beginners – 37-hour Cross Platform App Development Tutorial](https://www.youtube.com/watch?v=VPvVD8t02U8).
Also see the GitHub repo for this course at:
[https://github.com/vandadnp/mynotes-course](https://github.com/vandadnp/mynotes-course)

Chapter 3 - Introduction to Dart from:
[37 hour flutter course, chapter 3](https://www.youtube.com/watch?v=VPvVD8t02U8&t=4482s)
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
Futures are data to be returned in the future. Uses asynchronous programming.

e.g.:

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
A function that returns a list of things but internally calculates that data in a simple way. Generators generate "iterables" marked with sync*and async*.

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

Example of calling a Generator:

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

Went over basic scaffold of project created by:

```bash
flutter create --org dev.tomcoffee mynotes
```

Looked at android, ios, test, about other folders and files that are included by default by flutter create.

Went over pubspec.yaml, including app name and description (I change mynotes default text. Discussed versions, environment, dependencies, dev_dependencies, and assets.

Also looked at `pub.dev`, including `firebase_core`.

Then, opened up a terminal in VS Code, and added the following dependencies:

```bash
flutter pub add firebase_core
flutter pub add firebase_auth 
flutter pub add cloud_firestore
flutter pub add firebase_analytics
```

Also, flutter_lints, dev_dependency, was out of date, so ran:

```bash
flutter pub outdated
flutter pub upgrade --major-versions
```

and then, in pubspec.yaml, it updated flutter_lints:

```bash
 flutter_lints: ^4.0.0
 ```

## Chapter 9 - iOS App Setup

To go directly to the video for chapter 9, see:
[Chapter 9 - iOS App Setup](https://www.youtube.com/watch?v=VPvVD8t02U8&t=20910s)

Went over Apple developer account, and profile and identifiers setup.

In the Apple app world, Certificates identify you, as a developer, Profiles are an identity for your app. Apple provides a cert for every app that comes from the App Store. An app id, is used by you and Apple to identify what app you're working on. They help with push notifications. Profiles are different between dev and prod "flavors" of an app. They dictate what an app can and can't do, like debugging. Can run live dev on an iPhone, for example, using Xcode. App ID identifies your app and its capabilities.

Also, discussed Key chain in Apple dev account. Cert creates a private key on your computer, so hooks to Apple. Private key is stored in key chain. Include dev and distribution cert. Also, key chain can be used outside the Apple app store, to distribute your app to a cloud host, have a different app store than Apple, and they can send your app to you. Different avenue to get apps on iOS.

Next, deleted existing certs and profiles. From local machine, and from Apple dev account via developer.apple.com.

As part of the setup process for Notes app, we deleted all Apple Dev certifications in our local keychain. On Mac, open Keychain Access, My Certificates tab, search "Apple Dev" if needed, and delete Apple Dev certs. Also, go to developer.apple.com/account and delete all existing certificates. Also, locally, go to `/User/yourusername/Library/MobileDevice/ProvisioningProfiles` and deleted the files there.

Next, create development certificate in Apple developer account. This allows us to test our app on a real device, e.g. iPhone. Created iOS app development cert. On second step on developer account website, go back to your Mac, open Keychain Assistant, and Keychain Access > Certificate Assistant > Request a Certificate from a Certificate Authority. Fill in company/dev email and your name. Then save to disk. The request created a private key, viewable in Keychain Access. File on desktop. Then go back to Apple dev account, and upload cert request file. Uploaded and then downloaded a cert file, opened and added to Keychain.

Then, create a production cert. In Apple dev account, new cert > iOS Distribution (App Store Connect and Ad Hoc). Same process as dev cert. Create request, upload, download cert file, add to keychain.

Next steps, create Identifier in Apple dev account. New Identifier. Select App ID. Enter a description. For Bundle ID, use explicit, and use the org you specified when you created the app, e.g. dev.tomcoffee.mynotes. Then select capabilities in dev account for App ID, e.g. Push Notifications. For this app, skip, continue. Registering an app ID sets it up so no one else can use that identifier.

Debug on Real Device

First, get device id, UUID. Plugin device into Mac. Go to Finder. Select device. At top, hidden selection, click device name, and it rotates between serial number, model number, etc. Click again, UDID, etc. Go to App dev account, Devices, Add Device. Can also do from Xcode.

In Apple dev account, create Profile. Select iOS App Development under Development. Select previously created app id, cert, and device. Give it Provisioning Profile name of MyNotes Dev Profile. Do same for distribution profile. After you download the provisioning files, copy them to `/User/yourusername/Library/MobileDevice/ProvisioningProfiles`.

Next, setup in Xcode. Go to app in VS Code, go to iOS folder, and reveal in Finder. Then, double click Runner.xcwowrkspace to open in Xcode. Select Runnder folder in top left, to to Target in right, select Runner with Flutter icon, select Singing & Capabilities tab, remove check next to "Automatically manage signing". Same for RunnerTests. Then go to Debug button/tab (next to Capability) and make sure "Automatically manage signing" in unselected, for iOS, Provision Profile, select MyNotes Dev Profile. Then go to Release button/tab, and setup Provisioning Profile as well with prod profile. 

After all then, can debug run from Xcode on device connected to Mac. Ran successfully for me. Build failed for presenter and he debugged. Needed to change iOS # for target build and fix with Coco Pods sp? Once a build has been done once, the build will be cached and it will build faster next time. MyNotes first build took several minutes for about 5700 files.

Now we can run our app from VS Code. Taking a long time, 157 seconds to build, plus some minutes to appear on iPhone. It worked!

## Chapter 10 - Android App Setup

[Vandad](https://github.com/vandadnp) mentioned simulators, for iOS, and emulators, for Android. The emulators try to recreate all the aspects of the Android on a host device. The simulator, does not. For example, an iOS simulator from 5 years ago would perform as the host machine performs, not the iOS device from 5 years ago.

Discussed install of ADB and scrcpy for mobile development. Install ADB before scrcpy.

See GH repo for scrcpy:
[https://github.com/genymobile/scrcpy](https://github.com/genymobile/scrcpy)

During presentation, when trying to run debug on Android phone, bug came up. Had to do with
running an old Android phone and the min version of the dependencies in the project. Similar
issue came up in previous iOS chapter. Had to change minSdkVersion in `build.gradle`. Also, 
had to run `flutter clean android` 
Another build error involving `--multidex flag`.

Also, disable screen sleeping. See Android developer settings for your phone.

*[ADB]: Android Debug Bridge

## Chapter 11 - Firebase Backend Setup

[Chapter 11 Video](https://www.youtube.com/watch?v=VPvVD8t02U8)

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