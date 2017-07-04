# Unit VS Integration Testing

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

## What is integration testing?

Integration testing is a part of the software development process where individual software modules are combined and tested as a group in multiple ways.

An integration test can be performed anywhere there is a coupling between two software systems.

**Example**

If you have to test the keyboard of a computer then it is a unit test but when you have to combine the keyboard and mouse of a computer together to see its working or not than it is an integration test.

Unit testing is a prerequisite to performing integration testing on a system.

### Why do it?

An integration test is done to demonstrate that different pieces of the system work together.

**Example**

Testing the API used by Amazon to communicate with UPS, to ensure that customer orders which are ready to be shipped are collected by UPS.

### Types of integration testing

The three main integration testing strategies are as follows:

### Top down integration

#### What:

Testing takes place from top to bottom, following the control flow or architectural structure (e.g. starting from the GUI or main menu). Components or systems are substituted by stubs.

#### Advantages

very consistent because the integration testing is basically performed in an environment that almost similar to that of reality

#### Disadvantages

Basic functionality is tested at the end of cycle

### Bottom-Up Integration

#### What

Testing takes place from the bottom of the control flow upwards.

#### Advantages

Testing can be done together so that the product or application will be efficient and as per the customer specifications.

#### Disadvantages

We can catch the Key interface defects at the end of cycle

It is required to create the test drivers for modules at all levels except the top control

### Big Bang

#### What

In Big Bang integration testing all components or modules are integrated simultaneously, after which everything is tested as a whole

#### Advantages

Saves time.

#### Disadvantages

A lot riskier because it is very difficult to trace causes of failures.

### When would you use each kind of test?

Whilst unit tests ensure the functionality of small chunks of code such as functions and objects, integration tests are concerned with the interaction of larger units such as the interaction of modules, or the functioning of software when a database is included. Thus unit testing takes place early in the development process, and integration testing can only begin later.

* Unit tests are used during the initial phase of development, typically as part of TDD.
* Integration Tests can be used once significant modules have been written. If:
    - the lower level components have been built, then bottom up (no simulation needed) testing can begin;
    - if there are still unfinished dependencies, these can be simulated.
