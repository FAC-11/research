## What is Unit Testing?

### Individual Units of Code
Typically a unit of code might be a function or a class.
For this reason it is important that code be written in small chunks ('units') which can be easily tested. If functions are too reliant on other functions or have side effects rather than returning something, testing may be difficult.

### Testing
When code is written in small 'units' which output a particular value it is relatively easy to write tests that check if, with a given input, it outputs the correct return value.

### A Simple Example

A testable unit of code:
```js
function sum(a, b) {
    return a + b;
}
```
A unit test:
```js
//test returns 'true' if test passed, and 'false' otherwise
function testSum() {
    return sum(1, 2) === 3;
}
```

### Test Driven Development
A common way in which unit testing is applied is as part of the [Test Driven Development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development). This is a programming methodology in which unit tests are first written, and only then code is written to make them pass; after this code may be refactored. TDD follows a cycle of: Red, Green, Repeat. Red refers to tests which do not pass, Green refers to when code has been written to make them pass, and Refactor refers to improvements made to simplify that code.

### Testing Frameworks
Although it is possible to write your own tests entirely (as in the example above), typically a Testing Framework is used. Testing Frameworks have various advantages such as:
* attractive and easy to understand output;
* clear structure for writing your tests;
* provides useful built in functions, such as ```deepEqual``` to compare every item in an array or object.
Javascript Testing Frameworks include Tape, QUnit, Jasmine and many more.

Most Testing Frameworks are quite similar. Below is an example testing the ```sum``` function defined above, but written using the QUnit framework.

In this example only one test is made in the ```Qunit.test()``` function, but multiple related tests could be placed here.

```js
QUnit.test('Test math operator function', function ( assert ) {
  assert.strictEqual(sum(1,2), 3, "sum(1,2) should return 3");
});
```