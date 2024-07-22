# SOLID Principles

## 1. Single Responsibility Principle (SRP)
A class should have only one responsibility or task. This ensures that each class has a single purpose, making the code easier to maintain and understand.

**Example:**
```ts
class UserService {
  addUser(user: User) { /* logic to add user */ }
}

class EmailService {
  sendEmail(email: Email) { /* logic to send email */ }
}
```
In this example, `UserService` is responsible for user-related operations, and `EmailService` handles email-related tasks.

## 2. Open/Closed Principle (OCP)
Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means you should be able to add new functionality without changing the existing code.

**Example:**
```ts
class Bird {
  layEgg() { /* lay egg logic */ }
}

class FlyingBird extends Bird {
  fly() { /* flying logic */ }
}

class Penguin extends Bird {
  swim() { /* swimming logic */ }
}
```
Here, `Bird` class can be extended to create more specific bird types without modifying the original `Bird` class.

## 3. Liskov Substitution Principle (LSP)
Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. This principle ensures that a subclass can stand in for its superclass.

**Example:**
```ts
class Bird {
  layEgg() { /* lay egg logic */ }
}

class FlyingBird extends Bird {
  fly() { /* flying logic */ }
}

class Penguin extends Bird {
  swim() { /* swimming logic */ }
}
```
`Penguin` can replace `Bird` in the code where `layEgg` is called, ensuring that the substitution does not affect the program's correctness.

## 4. Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use. Create specific interfaces for each role.

**Example:**
```ts
interface Menu {
  showMenu(): void;
}

interface VegMenu extends Menu {
  showVegDishes(): void;
}

interface NonVegMenu extends Menu {
  showNonVegDishes(): void;
}
```
In this example, `VegMenu` and `NonVegMenu` provide more specific interfaces, ensuring that clients only depend on the methods they use.

## 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions. This principle ensures that the code is loosely coupled and can be easily changed.

**Example:**
```ts
class Store {
  constructor(private paymentProcessor: PaymentProcessor) {}

  purchase(item: Item) {
    this.paymentProcessor.process(item);
  }
}

interface PaymentProcessor {
  process(item: Item): void;
}

class StripePaymentProcessor implements PaymentProcessor {
  process(item: Item) { /* Stripe payment logic */ }
}

class PayPalPaymentProcessor implements PaymentProcessor {
  process(item: Item) { /* PayPal payment logic */ }
}
```
Here, `Store` depends on the `PaymentProcessor` interface, not on a specific payment method. This makes it easy to change the payment method in the future by implementing the `PaymentProcessor` interface.

By following these SOLID principles, your code will be more maintainable, extensible, and scalable.
