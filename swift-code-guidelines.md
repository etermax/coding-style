# Coding style guidelines for Swift
The main purpose of these guidelines is to improve code quality and readability, and to reduce the time we spend in code review by creating standard rules about code style.

 Because these Coding style guidelines follow [Swift API Design Guidelines](https://swift.org/documentation/api-design-guidelines/ "Swift API Design Guidelines"), Etermax developers should read those Official Guidelines first in order to understand the specifics goals of Swift as a programming language. In addition to the more detailed remarks in those official rules, these Coding Style Guidelines make complimentary remarks and specific requirements that guide our work as developers.


# Table of contents
* [1. Naming](#Naming)
  * [1.1. General](#General)
  * [1.2. Variables](#Variables)
  * [1.3. Functions](#Functions)
  * [1.4. Classes](#Classes)
  * [1.5. Protocols](#Protocols)
* [2. Code Style](#CodeStyle)
  * [2.1. General](#GeneralStyle)
  * [2.2. Optionals](#Optionals)
  * [2.3. Using ``guard``](#UsingGuard)
  * [2.4. Functions](#FunctionsStyle)
  * [2.5. Using ``.map()``, ``.flatMap()`` and ``.filter()``](#UsingMap)
* [3. Organization and Code Formatting](#Organization)
  * [3.1. Xcode Project Folders](#Xcode)
  * [3.2. Marks](#Marks)
  * [3.3. Documentation and Comments](#Comments)
  * [3.4. Protocol Conformance](#ProtocolConformance)
  * [3.5. Spacing and punctuation characters](#Spacing)

# 1. Naming <a name="Naming"></a>

## 1.1. General <a name="General"></a>

* Avoid typos that make it difficult to find a certain variable, method or class in the project.

**Not recommended:**
```swift
tutotial
dissappearedView
retreivedInformation()
AccesibilityViewController
```
* Use American English. Example: color, not colour.

* Avoid using obscure, uncommon or ambiguous definitions. Don't use variables such as ``detachedCondo`` if you want to define ``house``, for example. Nevertheless, you can use these uncommon definitions if they are related to the app’s business rules.

* Use sufficient words to define a certain variable, method or class. Useful verbosity is better than ambiguity.

Recommended | Not recommended
--- |---
``limitedFacebookIDs`` | ``limited50FBIds``
``limitedFriends`` | ``limited50Arr``
``removeAtIndex(1)`` | ``remove(1)``

* Use one word to define same concept, object or behavior in the project. If you are using ``get`` to name a method that returns certain object or information, you cannot use ``retrieve`` and ``fetch`` to name other methods with same behavior. Example: ``remove`` and ``delete``.

* Avoid using nonstandard abbreviations in your variables, methods or class names.

Recommended | Not recommended
--- |---
``repeatedPassword`` | ``repeatedPass or rptPass``
``userInfo`` | ``userInf``
``error`` | ``err``
``placeDescription`` | ``placeDesc``

* Use acronyms uniformly upper- or lower-cased according to its position in a variable or method. If the acronym is at the beginning of a variable or method, it should be lower-cased. In every other case, it should be upper-cased.

Recommended | Not recommended
--- |---
``urlString`` | ``URLString``
``currentURL`` | ``currentUrl``
``urlWith()`` | ``URLwith()``

But If the acronym is part of a class name, it always should be upper-cased, without considering its position.

Recommended | Not recommended
--- |---
``URLBuilder`` | ``UrlBuilder``
``CustomHTMLParser`` | ``CustomHtmlParser``


## 1.2. Variables <a name="Variables"></a>

* Use nouns to define variables, not verbs.

* Use ``lowerCamelCase`` naming convention to define your variables and properties. It includes all the constants that are created.

Recommended | Not recommended
--- |---
``placeholder`` | ``placeHolder``
``url`` | ``URL``

* Use plural nouns to define collection type variables.

Recommended | Not recommended
--- |---
``accounts`` | ``groupOfAccounts``
``recentlyPlayedWords`` | ``recentlyPlayed``

* Avoid including the object type name in the variable. It can be done only if it is useful to reduce ambiguity.

Recommended | Not recommended
--- |---
``name`` | ``nameString``
``isHidden`` | ``isHiddenBoolean``
``errorDescription`` | ``error (String)``
``tableView``, ``headerView``  |  

* Use boolean methods and properties as assertions about the receiver.

Recommended | Not recommended
--- |---
``view.isHidden()`` | ``view.hidden()``
``self.isWIFIAvailable()`` | ``self.wifiAvailable()``

## 1.3. Functions <a name="Functions"></a>

* Use English phrases to make a functions more readable.

Recommended | Not recommended
--- |---
``clearAnswers()``| ``answersClean()``


* Use "make" as beginning of names of factory methods. The first parameters should be included in function name.

Recommended |  Not recommended:
--- | ---
``makeFriend(with:name)``	| ``make(friendWithName:name)``

* Avoid using prefixes in the name of a method, be it the project’s name, the company’s name, or any other name.

* Avoid using labels in the arguments of a function that would cause repetition. Similarly, avoid labels when arguments cannot be distinguished one from another.

Recommended |  Not recommended:
--- | ---
remove(student) | removeStudent(student)
remove(student, at: classroom) | removeStudent(student, classroom: classroom)
minimumGRE(student1, student2) | minimumGRE(studentOne: student1, studentTwo: student2)

## 1.4. Classes <a name="Classes"></a>

* Use ``CamelCase`` naming convention to name a class.

* Avoid using prefixes to name a class. Example: ``KLLoginViewController``.

* Give a class an appropriate name according its role and responsibility. Avoid names such as Manager, Helper, Utilities and similar names that includes a variety of responsibilities.

## 1.5. Protocols <a name="Protocols"></a>

* Use ``CamelCase`` naming convention to name a protocol.

* Avoid including ``Protocol`` (or ``Delegate``) in the protocol name.

Recommended | Not recommended
--- |---
``clearAnswers()``| ``ReloginDelegate``

* Use nouns to define a protocol, if this protocol defines what an object is (or can be). Example: ``TableViewDataSource`` or ``RandomAccessCollection``.

* Use suffixes ``-able``, ``-ible``, or ``-ing`` (Example: ``Equatable``, ``Mappable``, ``Processing``) to describe a protocol capability.

# 2. Code Style<a name="CodeStyle"></a>

## 2.1. General<a name="GeneralStyle"></a>

* Use ``let``over ``var``.

* Use shortcut versions of type declarations instead of the full generic syntax.

Recommended | Not recommended
--- |---
var students: [Student] | var students: Array<Student>

* Delete every piece of dead code in your classes, even when they are automatically created methods by Xcode, such as didReceiveMemoryWarning() method.

## 2.2. Optionals<a name="Optionals"></a>

* Avoid using force unwrapping, ``as!`` and ``try!``.Use implicitly unwrapped optionals only with ``@IBOutlets``. In other cases, use a non-optional or regular optional properties.

* Check optional values against nil, when you are not going to use the value stored in this optional.

* Use the same name for the unwrapped constant or variable.

## 2.3. Using ``guard``<a name="UsingGuard"></a>

* Use ``guard`` as early return, instead of a ``if-else``.

## 2.4. Functions<a name="FunctionsStyle"></a>

* Avoid including more than four arguments in a function. If more arguments are needed, analyze possibility of creating an object.

## 2.5. Using ``.map()``, ``.flatMap()`` and ``.filter()``<a name="UsingMap"></a>

* Use ``.map()``, ``.flatMap()`` and ``.filter()`` to iterate a collection and to transform it into another one.

# 3. Organization and Code Formatting<a name="Organization"></a>

## 3.1. Xcode project folders<a name="Xcode"></a>

* Avoid differences between groups file created in Xcode Project file and the filesystem. The groups must be a reflection of folders in the filesystem.

## 3.2. Marks <a name="Marks"></a>

* Use MARK to separate different sections in a class, if necessary to make code more readable.

Mark type | Usage
--- |---
// MARK:  | Use it to create a single line above.
// MARK: Subtitle  |	Use it to create a subtitle to separate a section.
// MARK:- Subtitle  | Use it to create a subtitle and a single line to separate a section.

* Use ``//TODO`` and ``//FIXME`` to indicate technical debt or future refactor. Remember that both are just temporary measures and both marks must be deleted after resolving the issue. Leaving messages like these can mislead other developers in your team.

## 3.3. Documentation and Comments <a name="Comments"></a>

* Try to give good and informative comments. If the method, variable or class purpose is evident because of their names, consider not to write comments for them.

* Make brief comments. If you have to over-explain a method, variable and class, maybe you have a naming issue.

## 3.4. Protocol Conformance <a name="ProtocolConformance"></a>

* Use a separate class extension for the protocol methods, when a protocol conformance is added to a class.

**Recommended:**
```swift
class AnswersViewController: UIViewController {
}

extension AnswersViewController: CompositionFormProtocol {
}
```

**Not recommended:**
```swift
class AnswersViewController: UIViewController, CompositionFormProtocol {
}
```

## 3.5. Spacing and punctuation characters <a name="Spacing"></a>

* Use tabs for indentation, not spaces.

* Use one space after punctuation characters ( . , : ) and first brackets.

* Use open method braces and other braces (``if/else/switch/while etc``) on the same line as the statement.

* Avoid using semicolons at the end of line.

* Parentheses around conditionals **are not required** and should be omitted.

**Recommended:**
```swift
if index < currentIndex {
   direction = UIPageViewControllerNavigationDirection.Reverse
} else {
   direction = UIPageViewControllerNavigationDirection.Forward
}
```

**Not recommended:**
```swift
if (index < currentIndex) {
   direction = UIPageViewControllerNavigationDirection.Reverse;
}
else {
   direction = UIPageViewControllerNavigationDirection.Forward}
```
