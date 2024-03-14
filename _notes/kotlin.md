---
title: Kotlin Notes
date: 2024-03-07
---

## Functions

- Functions are defined with the `fun` keyword
- Every program needs a `main` function
  - This is a function named `main` with the optional parameter `args: Array<String>` for the command-line arguments
- [Single-expression functions](https://kotlinlang.org/docs/idioms.html#single-expression-functions)
  - Also known as compact functions
  - If the body consists of a single expression, a single-expression function can be used by avoiding the braces and using `=` between the function signature and the function body
  - Example:
    ```kotlin
    fun isTooHot(temperature: Int) = temperature > 30
    ```
- [Lambdas](https://kotlinlang.org/docs/lambdas.html)
  - Syntax:
    ```
    { <args>... -> <body> }
    ```
  - The return type does _not_ need to be specified in a Lambda expression
  - If there is only a single argument, `<args>...` and `->` can be omitted and the argument can be accessed as [`it`](https://kotlinlang.org/docs/lambdas.html#it-implicit-name-of-a-single-parameter)
- [Higher-order functions](https://kotlinlang.org/docs/lambdas.html#higher-order-functions)
  - Functions that take one or more functions as arguments or return a function
  - Function arguments can be passed as function references or lambdas
  - By convention, function parameters should go last in a higher-order function's parameter list
  - [Function reference](https://kotlinlang.org/docs/reflection.html#function-references)
    - Way of referring to an existing function without invoking the function
    - Formed by prepending `::` to the function name and omitting the parentheses
    - Example:
      ```kotlin
      list.map(::double)
      list.map(Math::decrementExact)
      ```
  - [Trailing lambda invocation](https://kotlinlang.org/docs/lambdas.html#passing-trailing-lambdas)
    - If the last parameter of a higher-order function is a function parameter, then a lambda expression can be passed to this parameter _outside_ of the funciton invocation's parentheses
    - Example:
      ```kotlin
      list.fold("Foo") {acc, i -> "$acc $i"}    // Equivalent
      list.fold("Foo", {acc, i -> "$acc $i"})   // Equivalent
      ````
    - Only _one_ lambda expression can be passed in this way
    - If the higher-order function has only a single argument, then the parentheses can be omitted entirely
      - Example:
      ```kotlin
      list.filter {it > 10}   // Equivalent
      list.filter({it > 10})  // Equivalent
      ```
- [Inline functions](https://kotlinlang.org/docs/inline-functions.html)
  - A lambda function for which each invocation is transformed by the compiler into direct exeuction the lambda's body
    - By default, lambdas are objects (deriving from [`Function`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-function.html) with an `invoke()` method)
  - Reduces the overhead of treating lambdas as objects
  - Defined by prepending `inline` to the function name

## Variables

- Constants can be defined with the `val` keyword
- Variables can be defined with the `var` keyword

## Type declarations

- Declaring types of variables is optional
- Once a type has been assigned to a variable, it can't be changed

## [Nullability](https://kotlinlang.org/docs/null-safety.html)

- By default, variables with an explicit type cannot be assigned `null`
- To make variables with an explicit type accept `null`, append `?` to the type
- For example:
  ```
  val a: Int? = null
  val l: List<Int>? = null
  ```
- Variables without an explicit type can be assigned `null` if no type has been inferred for this variable yet (i.e. if `null` is the first assignment to the variable)
  - Type is in that case inferred as `Nothing?`
- The `?` operator can be used to test expressions for `null`
  - For example:
    ````kotlin
    Math.round(10.1)?.plus(1)
    ````
  - If the expression is `null`, the entire statement returns `null`, otherwise the statement is executed as usual
- The `?:` operator ([Elvis operator](https://kotlinlang.org/docs/null-safety.html#elvis-operator)) can be used to customise the null return value of an expression tested with `?`
    - For example:
    ```kotlin
    Math.round(10.1)?.plus(1) ?: "foo"
    ```

## [Control flow](https://kotlinlang.org/docs/control-flow.html)

- Use `else if` for an `if` statement with multiple options (no dedicated `elseif/elif` keyword)
- The [`when`](https://kotlinlang.org/docs/control-flow.html#when-expression) statement allows testing for multiple options too
  - Similar to the Bash `case` statement, but more flexible
  - Examples:
    ```kotlin
    // With argument
    when (list.size) {
        in 0..4 -> println("Length is less than 5")
        5, 6 -> println("Length is 5 or 6")
        else -> println("Length is more than 6")
    }
    // Without argument
    when {
        list.size < 5 -> println("Length is less than 5")
        list.size == 5 || list.size == 6 -> println("Length is 5 or 6")
        else -> println("Length is more than 6")
    }
    ```
- Loops can be created with the `for`, `while` and `do..while` keywords
- The `repeat()` function can be used to repeatedly execute a function
  - For example:
    ```kotlin
    repeat(3, { println(it) })
    ```
  - The current index (starting at 0) is passed as an integer to each invocation of the function
- Ranges can be created with `..`, `downTo`, and `step`
  - For example:
    ```kotlin
    1..4
    10 downTo 0 step 2
    ```
  - Ranges can be used in conjunction with the `in` keyword to be used in an `if` or `when` statement or in a `for` loop

## Strings

- Enclosed in double quotes (`"`)
  - Single quotes (`'`) are used for the [characters](https://kotlinlang.org/docs/characters.html)) data type
- [Multiline strings](https://kotlinlang.org/docs/strings.html#multiline-strings) are enclosed in `"""`
- [String templates](https://kotlinlang.org/docs/strings.html#string-templates)
  - Strings with interpolated variables and expressions using `$` or `${...}`
  - For example:
    ```kotlin
    "Hello $variable"
    "Hello ${Math.round(10.1)}"
    ```

## Pairs and Triples

- Pairs can be created with `to`:
  ```
  <expression> to <expression>
  ```
- Triples can be created with `Triple()`
  ```
  Triple(<expression>, <expression>, <expression>)
  ```
- Elements can be accessed with `first`, `second`, and `third`, respectively
  - For example:
  ```kotlin
  val pair = "foo" to 100
  println(pair.second)
  ```
- Elements do not need to be of the same type
- Pairs and Triples can be destructured to 2 or 3 variables
  - For example:
  ```kotlin
  val pair = "foo" to 100
  val (p1, p2) = pair  // p1 <= "foo", p2 <= 100
  ```

## [Arrays](https://kotlinlang.org/docs/arrays.html)

- Arrays can be created with `arrayOf()`:
  ```kotlin
  arrayOf(1, 2, 3)
  ```
- Mutability:
  - ✅ Update, ❌ Add, ❌ Remove
- Array is a basic data type (i.e. like Int, Float, String, etc.)
- If there is no specific requirement for the Array data type, use List because it's more flexible

## [Lists](https://kotlinlang.org/docs/collections-overview.html#list)

- [List](https://kotlinlang.org/docs/collections-overview.html#list), [Set](https://kotlinlang.org/docs/collections-overview.html#set), and [Map](https://kotlinlang.org/docs/collections-overview.html#map) form the [collections](https://kotlinlang.org/docs/collections-overview.html) type group
  - List and Set inherit from the [Collection](https://kotlinlang.org/docs/collections-overview.html#collection) interface, [Map](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/) is a separate interface with several implementations such as [HashMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-hash-map/)
- _Immutable_ lists can be created with `listOf()`
  - ❌ Update, ❌ Add, ❌ Remove
- _Mutable_ lists can be created with `mutableListOf()`
  - ✅ Update, ✅ Add, ✅ Remove

## [Map](https://kotlinlang.org/docs/collections-overview.html#map)

- Map itself is an [interface](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/) with various implementation such as [HashMap](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-hash-map/)
- HashMaps can be created with `hashMapOf()` by supplying one or more Pairs
  - For example:
  ```kotlin
  val m = hashMapOf("one" to 1, "two" to 2, "three" to 3)
  ```
- HashMap values can be accessed with square brackets
  - For example:
  ```kotlin
  m["one"]
  ```
- Values can also be retrieved with the [`get()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/get.html), [`getOrDefault()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/get-or-default.html), or [`getOrElse()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/get-or-else.html) functions

## Coding style

- [Kotlin style guide](https://developer.android.com/kotlin/style-guide)
- Use camel case (with an initial lower-case letter) for identifiers
- Indent by 4 spaces

## Object-orientation

### [Primary constructor](https://kotlinlang.org/docs/classes.html#constructors)

- Allows passing parameters that can be used in property initialisers
- Defined between the class name and the opening curly brace of the class body
  - For example:
  ```kotlin
  class Person constructor(firstName: String) {
      val firstName: String = firstName.uppercase()
      ...
  }
  ```
- If the constructor has no modifiers, the `constructor` keyword can be omitted
  - For example:
  ```kotlin
  class Person(firstName: String) {
      val firstName: String = firstName.uppercase()
      ...
  }
  ```
- When parameters are used as-is for object properties, the properties can be directly defined in the primary constructor with `val` and `var`
  - For example:
  ```kotlin
  class Person(val firstName: String) {
      ...
  }
  ```

### Initialiser blocks

- Allow to run arbitrary code during object initialisation
- Defined with the `init` keyword
  - For example:
  ```kotlin
  class Person(firstName: String) {
      val firstName: String = firstName.uppercase()
      init {
        println("First name is ${this.firstName}")
      }
      ...
  }
  ```
- Run immediately after running the primary constructor together with the property initialisers in the order in which they are defined in the class
- Can access the primary constructor parameters and the object properties that have been initialised so far
  - Use `this` to explicitly access object properties

### [Secondary constructors](https://kotlinlang.org/docs/classes.html#secondary-constructors)

- A class can have any number of secondary constructors
- Secondary constructors allow defining alternative ways of initialsing an object
- Defined in the class body with the `constructor` keyword
  - For example:
  ```kotlin
  class Person(val firstName: String) {
      var firstName = firstName.uppercase()
      constructor(firstName: String, code: Int): this(firstName) {
          if (code == 1) this.firstName = "**root**"
      } 
  }
  ```
- Each secondary constructor must include a call to the primary constructor after the argument list
  - The primary constructor is referred to as `this` after the parameter list separated by a colon (`:`)
  - The call must include all non-optional parameters of the primary constructor
  - The call is executed before starting the execution of the secondary constructor
  - The execution of the primary constructor includes the execution of all initialiser blocks and property initialisers
- The call to the primary constructor can be omitted if the class does not define an explicit primary constructor
  - In that case, any initialiser blocks and property initialisers are still executed before running the secondary constructor
- As a best practice, use the factory pattern instead of secondary constructors

### [Object properties](https://kotlinlang.org/docs/properties.html)

- Format (mutable property):
  ```
  var <name> [: <type>] [= <initialiser>]
    [<get()>]
    [<set(value)>]
  ```
- Format (read-only property):
  ```
  val <name> [: <type>] [= <initialiser>]
    [<get()>]
  ```
- Type can be omitted if it can be inferred from the initialiser or the return type of the getter
- Properties are accessed as `<object>.<name>`
- Each property has a default getter and setter that returns the properties value as-is, or assigns the provided value to the property as-is:
  ```kotlin
  obj.prop          // Default getter
  obi.prop = "foo"  // Default setter
  ```
- These default getters and setters may be replaced with custom getters and setters defiend with `get()` and `set()`, respectively:
  - `get()` is a function that must return a value
    - May be a single-expression function
  - `set(value)` is a function that receives the value of the assignment statement and in turn assigns values to object properties
  - When referring to its own property in `get()` or `set(value)`, then `field` must be used instead of the property name
  - For example:
  ```kotlin
  class Foo(mutable: Int, immutable: Int) {
      var mutable: Int = mutable
          get() = field * 2      // 'field' refers to 'mutable'
          set(value) {
              field = value / 3
          }
      val immutable: Int = immutable
          get() = field * 2      // 'field' refers to 'immutable'
  }

  fun main() {
    foo = Foo(10, 10)
    println(foo.mutable)    // Prints '20'
    println(foo.immutable)  // Prints '20'
    foo.mutable = 12        // Assigns 4
    println(foo.mutable)    // Prints '8'

  }
  ```
  - The argument name in `set(value)` is `value` by convention, but it may be any valid name

### [Abstract classes](https://kotlinlang.org/docs/classes.html#abstract-classes)

- A class that cannot be instantiated but only inherited from by other classes
- May contain both functions and properties that are either unimplemented/unassigned (abstract) or implemneted/assigned 
- Contains a primary constructor

### [Interfaces](https://kotlinlang.org/docs/interfaces.html)

- Can be implemented by other classes
  - Classes may implement one or more interfaces
- An interface may implement another interface
- May only contain unimplemented/unassigned functions and properties
- When implementing multiple interfaces, results in composition
  - Composition is preferred over inheritance through e.g. abstract classes

### Special types of classes and objects

- [Data classes](https://kotlinlang.org/docs/data-classes.html)
  - Declared with `data class`
- Singleton classes
  - Declared with `object` (instead of `class`)
- [Enums](https://kotlinlang.org/docs/enum-classes.html)
  - Declared with `enum class`
- [Sealed classes](https://kotlinlang.org/docs/sealed-classes.html)
  - A class that can be subclassed but only in the same file
  - The point of this is that the compiler knows all subclasses at compile time and thus can do extra checks
  - Declared with `sealed class`

### [Extension functions and properties](https://kotlinlang.org/docs/extensions.html)

- Define new functions or properties for a class in a separate file without having to inherit from this class or even having to have access to the source code of this class
  - Also works for interfaces
- Format:
  ```kotlin
  <Class>.<name>()
  ```
- For example:
  ```kotlin
  fun String.hasSpaces(): Boolean {
    return this.find { it == ' ' } != null
  }
  ```

### [Generics](https://kotlinlang.org/docs/generics.html)

- By convention, if there is a single generic type, it is called `T`
  - There are some special case conventions for classes with generic types, such as `K` and `V` (key and value) for Maps, and `E` for Lists
- The default type for a generic type is `Any?` (nullable)
- Generic types can be restricted to `in` and `out` variances
  - `out`: if a generic type is restricted to `out`, then, after initialising the object with this generic type, the generic type can only be _returned_ from the object,  but no object of this generic type can be passed into the object
    - For example, in an immutable [`List<E>`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/), the generic type `E` is an `out` variance because `E` objects can only be retrieved from the list (after the list has been initialised) because it's an immutable list
    - Also known as the class being a _producer_ of the generic type, or the class being _covariant_
  - `in`: if a generic type is restricted to `in`, then objects of this generic type can only be passed into the object but cannot be retrieved from the object
    - For example, in a [`Comparable<T>`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-comparable/), the generic type `T` is an `in` variance because it can onyl be passed _into_ the object (to the `compareTo()` function) but is never returned from the object
    - Also known as the class being a _consumer_ of the generic type, or the class being _contravariant_
  - The reason for these `in` and `out` variances are sub-type and super-type conversions:
    - `out`: can assign to super-type variable: a `List<out Double>` object can be assigned to a variable of type `List<Number>` (`Number` is a super-type of `Double`) because there is no way that this variable of type `List<Number>` can be used to put a `Double` into the list
    - `in`: can pass in sub-type objects: a `Double` can be passed into a `Comparable<in Number>` (`Double is a sub-type of `Number`) because there is no way that the `Comparable<Number>` must return a `Double` again
- [Generic functions](https://kotlinlang.org/docs/generics.html#generic-functions)
  - Functions with a parameter of a generic type
    - For example:
    ```kotlin
    fun <T> myFunction(foo: T) {
    ...
    }
    ```
  - To call a generic function, the generic type is specified after the function name
    - For example:
    ```kotlin
    myFunction<String>("foo")
    ```
- [Type erasure](https://kotlinlang.org/docs/generics.html#type-erasure), [`inline`](https://kotlinlang.org/docs/inline-functions.html), and [`reified`](https://kotlinlang.org/docs/inline-functions.html#reified-type-parameters)
  - Making generic types (e.g. `T`) available at runtime instead of just compile time (for example, for type checks with `is`)
  - The fact that, by default, generic types are only available at compile time and not at runtime is called "type erasure"
