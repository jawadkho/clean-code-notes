# Day 1

* Everytime you checkout code make it better in some way.
  * Don't react to broken code or fear to touch it.
  * Refactor
  * A green button removes fear (i.e. tests that you trust).
* Finals in local variables are just noise and the compiler isn't able to use them for the vast majority of usecases.
* Variable name length should be proportionate to scope.
  * Same applies to functions.
    * However, function name gets smaller the more general the function becomes.
* Avoid 'data' and 'info' (etc) subtypes. For example:
  * Product, ProductData and ProductInfo.
    * How can you tell what the difference is? It's difficult.
* Avoid noise words: Manager, Data, Info etc.
* If constructor isn't clear, use factory method:
  * `new Complex(23.4)` -> `Complex.FromRealNumber(23.4)`
* Short Pairing is better than long pairing.
  * Paper: "Promicious Pairing"
    * Shows that long term pairing causes people to comprmise for each other.
  * Suggestion: Pair half the day (> 20% & < 80%).

# Day 2

* A function should do one thing.
  * A function  does not do one thing if you can **meaningfully** extract a function out.
* Don't test (business logic) through the GUI.
  * Side-Note: See Enzyme for ReactJS.
* TODO: Search for Atom plugin to do with "Widen Selection".
* **Demeter's Law**: Don't let a line become a focus.
  * That is, it should have too much knowledge of many classes.
  * rental.getMovie().getTitle() -> rental.getMovieTitle()
  * Strings in tests should use an appropriate name:
    * `new Customer("Customer Name")` as opposed to `new Customer("Fred")`
* You *should* refactor unit tests.
  * Or else one by one you will lose tests (because, for example, they may get complicated and abandoned).
  * Without unit tests you will have less of an ability to refactor your code.
* **Step Down Rule**: Every function should exit at a level of abstraction below the current function.
* Switch statements are fundamentally dangerous, especially as they scale. It's similar to why using `instanceof` is bad. Use polymorphism instead.
* You don't need to do one to one coupling of test classes to regular classes.
  * The objectives should be to check behaviour and to cover all lines of code (however, 100% coverage isn't realistic and totally meaningful).
* Use Red-Green-Refactor - TDD.
* The test (in the diagram below) should check all behaviours and lines.
```
                                   +--+
                                +->|c1|
          +                     |  +--+
+------+  |   +-------+   +-----+
|      |  |   | class |   |     |  +--+
| test +----->+ cA    +-->+ cB  +->|c2|
|      |  |   |       |   |     |  +--+
+------+  |   +-------+   +-----+
          +                     |  +--+
                                +->|c3|
                                   +--+
```
* Mocking should be done at architectural boundaries (of-the-hand est. ~1/10)
* See Mutation Testing (e.g. ++ -> --).
* Change dependencies. See below: Have A depend upon the Interface B (InB) rather than directly on B, the agreement.
```
+---+   +---+      +---+    +---+    +---+
| A +-->+ B | ===> | A +--->+InB+<---+ B |
+---+   +---+      +---+    +---+    +---+
```

# Day 3

* Robert's Rule: 3 arguments max.
  * Same for constructor.
  * Anything more could (or rather should) be a datastructue.
  * Could use a setter (for anything more than 3).
  * He doesn't like the idea of an *output* arguments.
  * Usually (but not always) booleans are disliked. It's not always clear what the boolean means.
    * Two booleans are a no-no.
* Side-Effect functions are things that change state e.g. open() & close(). Functions that come in pairs.
  * Garbage collection is a result of inability to work well with pair functions (i.e. new ... & delete ...).
  * Use language helpers such as below (Java) or use the callback design.
  ```
  try (File f = open('/some-file.txt')) {
    doSomething(f);
  }
  ```
* Try/Catch
  * Should be that main focus in a function.
  * Should be the first line of function.
  * Should be a single line:
    ```
    try {
      doSomething();
    } catch (Exception e) {
      log(e);
    }
    ```
  * Don't throw errors far up the stack.
  * Translate an exception as it goes up. Hide it behind abstractions.
    * IndexOutOfBoundsException -> SomeMoreInformativeException
* TDD Rules
  * 1) You are not allowed to write production code without a failing unit test.
    * Failing includes no compiling.
  * 2) You are not allowed to (continue to) write a unit test if it is failling.
  * 3) You are not alloed to write production code if the unit tests are passing.
* TDD (is basically) Double Entry Book Keeping.
  * In Double Entry Book keeping it would be a laughable statement to say to do credits now and debits later.
  * However, in software engineering it would be to say a similar statement: production now and tests later.

## Comments
* A comment is not a reason to not fix something. For example: 'This will never equal to 3'.
  * Rule: See every comment as a failure.
* Comment Lie:
  * The rot silently.
  * They can get migrated without thought and no longer fit or make sense.
* Good (or okay) comments:
  * Copyrights.
  * When fighting a design pattern naming scheme, for example, if you can't use `productInstance()` because the word Instance is being used as part of another pattern.

## Sizes
* File Sizes should typically be between 40 and 100 and all should be less than 500. JUnit was used as an example for this.
* Line length should typically be between 80 and 120.
* "Architecture is about intent" - the architecture should show the intention rather than forcefully fitting in the code or project.
  * It shouldn't dictate the application.
