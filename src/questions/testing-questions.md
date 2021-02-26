---
title: Testing Questions
layout: layouts/page.njk
permalink: /questions/testing-questions/index.html
---

* What are some advantages/disadvantages to testing your code?
  - Pros:
    - The tests give you confidence that nothing's broken
    - Having unit tests will allow you to test your functions in isolation, theyreby helping you pinpoint which function has a problem when trying to debug
    - When you drive your code through tests, you will end up writing testable code, which is cleaner and more maintainable
  - Cons:
    - spend more time writing tests

* What tools would you use to test your code's functionality?
  - Jest, Chai, Mocha, Artillery.io, Loader.io, New Relic, Chrome DevTools, React DevTools

* What is the difference between a unit test and a functional/integration test?
  - Unit tests are very low level, close to the source of your application. They consist of testing individual methods and functions of the classes, components, or modules used by your software. Unit tests are in general quite cheap to automate and can be run very quickly by a continuous integration server.
  - Functional tests focus on the business requirements of an application. They only verify the output of an action and do not check the intermediate states of the system when performing that action.
  - Integration tests verify that different modules or services used by your application work well together. For example, it can be testing the interaction with the database or making sure that microservices work together as expected. These types of tests are more expensive to run as they require multiple parts of the applicaiton to be up and running.
    - There is sometimes a confusion between integration tests and functional tests as they both require multiple components to interact with each other. The difference is that an integration test may simply verify taht you can query the database while a functional test would expect to get a specific value from the database as defined by the product requirements.
  - End-to-end testing replicates a user behavior with the software in a complete applicaiton environment. It verifies that various user flows work as expected and can be as simple as loading a web page or logging in or much more complex scenarios verifying email notifications, online payments, etc.
    - End-to-end tests are very useful, but theyre expensive to perform and can be hard to maintain when they're automated. It is recommended to have a few key end-to-end tests and rely more on lower level types of testing (unit and integration tests) to be able to quickly identify breaking changes.

* What is the purpose of a code style linting tool?
  - flagging bugs in your code from syntax errors
  - Provide suggestions for common best practices
  - Diminish unused code
  - consistent code style
  - lets code be more maintainable

* What are some of the testing best practices?
  - Good mixture of lower level and higher level tests (unit tests, integration tests, e2e tests)
  - Design tests to be independent form one another
  - Make tests independent of the data source
  - good test descriptions
