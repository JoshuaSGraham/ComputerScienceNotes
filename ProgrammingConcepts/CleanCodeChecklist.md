#Clean-Code-Checklist

# Clean Code Checklist
 Use this short checklist when encountering code that you are unfamilliar with or while writing new code.

## General
- [ ] My code reads like a naratuve. I write code for humans, not machines.
- [ ] I document my code only when necessary. My code should speak for itself.
- [ ] I provide clear instructions on how to build and release my codebase. Where appropriate, I provide working build scripts/makefiles or CI/CD setup instructions.
- [ ] I use native functionalities instead of implementing my own libraries, unless for a very good reason.
- [ ] My code is consistent in its design patterns, documentation, and naming conventions. I do not change things mid-development and go against established patterns.
- [ ] I have added logging to my application, so I or other developers can debug when things go awry.

## Classes
- [ ] My class has the strictest access modifier possible.
- [ ] My class is named accurately.
- [ ] My class performs operations on only one specific object and, therefore, adheres to the single-responsibility principle.
- [ ] My class lives in the right folder within my project.
- [ ] If I struggle with implementing my class, I take a step back and come up with a brief description of the class and its intended functionality. This refocus can help write cleaner code. If my class should do multiple things, split it up.

## Methods
- [ ] My method has the strictest access modifier possible.
- [ ] My method is named accurately and correctly describes the logic within (leaving nothing out).
- [ ] My method performs only one general operation or collects information from other methods related to its operations. It adheres to the single-responsibility principle.
- [ ] If my method has a public access modifier, we do not perform any operations within the method. The public method calls other, smaller, methods and organizes the outputs.
- [ ] I have unit tests backing my method. The unit tests should cover the major success and failure logic branches.

## Variables, Fields, And Properties (VFP)
- [ ] My VFP types are of the most abstract type possible. If I can use an interface instead of a concrete type, I use the interface. This promotes polymorphism and the use of the Liskov substitution principle.
- [ ] I do not have any "magic numbers" assigned to a variable.
- [ ] Whenever possible, I restrict my VFPs to the tightest access modifier possible. If a VFP can be made read only, I make it read only. If a VFP can be made a constant, I make it a constant.
- [ ] I always validate my input arguments. This protects me against unwanted null pointer exceptions and operating on data in an invalid state.
- [ ] I use enums and constants instead of string literals where appropriate.

## Testing
- [ ] I always provide appropriate unit tests to my code.
- [ ] I follow test-driven development where possible.
- [ ] I am not focused on code coverage. My goal in testing is to protect against unexpected side effects and to validate my assumptions about the requirements and existing code.
- [ ] If one of my changes breaks a test, I fix the test.
- [ ] I always write the least amount of code necessary to satisfy all tests. Any extraneous lines increase the amount of code to maintain.