## Single Responsibility Principle (SRP)

A class should have only one reason to change, meaning it should have only one job or responsibility. This makes classes easier to understand, test, and maintain.

**Example**: Instead of having a `User` class that handles both user data and email sending, separate these into `User` and `EmailService` classes.

## Open/Closed Principle (OCP)

Software entities should be open for extension but closed for modification. You should be able to add new functionality without changing existing code.

**Example**: Use interfaces or abstract classes to allow new implementations without modifying existing code. A payment system can support new payment methods through interfaces rather than modifying the core payment class.

## Liskov Substitution Principle (LSP)

Objects of a superclass should be replaceable with objects of its subclasses without breaking the application. Subclasses must be substitutable for their base classes.

**Example**: If you have a `Bird` class with a `fly()` method, a `Penguin` subclass shouldn't throw an exception when `fly()` is called, as this violates the expected behavior.

## Interface Segregation Principle

No client should be forced to depend on methods it doesn't use. Create specific, focused interfaces rather than large, general-purpose ones.

**Example**: Instead of one large `Worker` interface with methods for all types of work, create separate interfaces like `Programmer`, `Designer`, and `Tester` with only relevant methods.

## Dependency Inversion Principle

High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details; details should depend on abstractions.

**Example**: A `NotificationService` shouldn't directly instantiate an `EmailSender`. Instead, it should depend on an `INotificationSender` interface, allowing different notification methods to be injected.

These principles work together to create code that's easier to maintain, extend, and test. They reduce coupling between components and increase cohesion within them, leading to more robust software architecture.