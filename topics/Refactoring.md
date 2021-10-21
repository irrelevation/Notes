# Refactoring

Refactoring should never change or add functionality. Make lots of little changes, not one big change.
The nice thing about this approach is that your code is never broken. You can stop at any point and commit into production.

Make refactoring a **constant effort**.
Whenever you come across a piece of code that should be refactored, do so immediately if possible.
You don't have to refactor the whole thing, but leave it better than you found it.

## Indicators for refactoring

**Code smells** are indicators that a piece of code needs to be refactored.

- long functions
- blank lines in functions
- abbreviations

## Types of refactoring

1. **Extract Function**
   - Put the block of code in a function. A function seperates your _intention_ from your _implementation_.
     Make shure to pass in any state needed of the context it was extracted from as parameters.
     Make shure to return any state needed in the code it was extracted from.
2. **Rename Variable**
3. **Inline Variable**
4. **Replace Temp with Query**
   - Extract Function
   - Inline Variable
   - Replacing the variable assignment with a query often allows you to pass less variables/state into functions.
5. **Change Function Declaration**
   - change parameters, often enabled by replacing a temporary variable with a query (4)
6. **Split Loop**
   - Split loops that are doing **more than one thing** into different loops. You will duplicate the looping logic. If you are worried about performance implications then _test_ the performance!
7. **Slide Statements**
   - Change the position of a statement (especially variable assignment) so it is next to the code it logically belongs to.
8. **Split Phase**
   - Produce a data structure
   - Do something with the data structure
