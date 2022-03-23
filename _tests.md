# Testing

* Structure your tests using the Arrange-Act-Assert pattern.
* Use test object builders to make test setup easy for commonly used objects.
* Evaluate a single concept per test.
* F.I.R.S.T. — Tests should be fast, independent (of each other), repeatable (on different systems/machines, self-validating (returning a boolean value), and timely.
* Make sure tests fail when they should.
* Remember your boundaries and edge cases.
* Test the things you’re most worried about going wrong

### Why do it?

* Protection - against introducing bug
* Confidence - to add changes, reuse and refractor
* Documentation
* Isolation - Unit tests force you to add isolation to enable testing
* Quality - promotes loose coupling since tightly coupled code is hard to test
* Industry Standard

### In Python

* Doctest - Test Documentation, document code you write for yourself
* py.test - for Unit testing
* Coverage - test your code coverage
* PyFlakes - checks for logical errors
* Hypothesis - Test Case Generator
* possibly some Linter