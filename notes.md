# Day 1

* Everytime you checkout code make it better in some way.
  * Don't react to broken code or fear to touch it.
  * Refactor
  * A green button removes fear (i.e. tests that you trust).
* Bogdan -> Finals suck.
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
    * Shows that long term pairing causes people to comprmise for each other. Think: MIR Writer.
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
