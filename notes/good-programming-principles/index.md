---
marp: true
theme: semusings
paginate: true
header: '© Software Engineering Musings - <https://semusings.dev/> - subscribe us on :yt: 📺 at <https://youtube.com/@semusings>'
footer: ''
---

# Good Programming Principles

---

## 🎙️ Intro

Hey everyone! Welcome back to **Software Engineering Musings**!

Today we're covering **Good Programming Principles** — simple rules that help you write clean, maintainable code.

👉 Don’t forget to **subscribe**: [youtube.com/@semusings](https://youtube.com/@semusings)  
👉 More content at: [semusings.dev](https://semusings.dev)

Let's dive in 👇

---

## 💡 General Programming Principles

- **KISS – Keep It Simple, Stupid**  
  ➤ Don’t overcomplicate.  
  ✅ *Example:*  
  Instead of:
  ```javascript
  if (isLoggedIn === true) { return true; }
  ```
  Just write:
  ```javascript
  return isLoggedIn;
  ```

- **YAGNI – You Aren’t Gonna Need It**  
  ➤ Don’t build things before they’re needed.  
  ✅ *Example:*  
  Don’t write dark mode support if it’s not a requirement yet.

- **Do the Simplest Thing That Could Possibly Work**  
  ➤ Start with the most basic working version.  
  ✅ *Example:*  
  Return static data from an API at first — wire it to a real DB later.

- **Separation of Concerns**  
  ➤ Keep logic split by responsibility.  
  ✅ *Example:*  
  Don’t put database logic inside a controller — move it to a service.

- **Code for the Maintainer**  
  ➤ Prioritize readability.  
  ✅ *Example:*  
  Use `calculateTotalPrice()` instead of `calc()`.

- **Avoid Premature Optimization**  
  ➤ Make it correct before making it fast.  
  ✅ *Example:*  
  Don’t parallelize image uploads unless performance is a problem.

- **Optimize for Deletion**  
  ➤ Write code that’s easy to remove or refactor.  
  ✅ *Example:*  
  Use a single-purpose class instead of adding logic to an unrelated one.

- **DRY – Don’t Repeat Yourself**  
  ➤ Reuse common logic.  
  ✅ *Example:*  
  Move repeated form validation code into a shared function.

- **Boy Scout Rule**  
  ➤ Leave code cleaner than you found it.  
  ✅ *Example:*  
  If you're editing a function, update the old comment that doesn’t make sense anymore.

---

## 🔗 Relationships Between Code Components

- **Connascence**  
  ➤ The degree to which changes in one piece of code require changes in another.  
  ✅ *Example:*  
  Avoid:
  ```javascript
  api.get('user_profile')
  ```
  Use:
  ```javascript
  api.getUserProfile()
  ```

- **Minimize Coupling**  
  ➤ Reduce dependencies between parts.  
  ✅ *Example:*  
  Don’t hardcode `PaymentService` inside your controller — inject it.

- **Law of Demeter**  
  ➤ "Talk to friends, not strangers."  
  ✅ *Bad:*
  ```javascript
  order.getCustomer().getAddress().getCity()
  ```
  ✅ *Good:*
  ```javascript
  order.getShippingCity()
  ```

- **Composition Over Inheritance**  
  ➤ Favor flexible building blocks.  
  ✅ *Example:*  
  Instead of:
  ```javascript
  class FlyingFish extends Fish
  ```
  Compose like:
  ```javascript
  class FlyingFish {
    constructor() {
      this.fish = new Fish();
      this.canFly = true;
    }
  }
  ```

- **Orthogonality**  
  ➤ Components should be independent.  
  ✅ *Example:*  
  Changing your logging system shouldn’t affect authentication.

- **Robustness Principle**  
  ➤ Be strict in what you send, lenient in what you receive.  
  ✅ *Example:*  
  Validate all inputs. Accept optional fields gracefully.

- **Inversion of Control**  
  ➤ Framework controls flow, not your app.  
  ✅ *Example:*  
  Register routes with Express, but don’t control the entire lifecycle manually.

---

## 🧱 Principles for Internal Code Structure

- **Single Responsibility Principle (SRP)**  
  ➤ A class/module should do one thing.  
  ✅ *Example:*  
  `UserRepository` handles DB logic, not email notifications.

- **Open/Closed Principle**  
  ➤ Open to extension, closed to modification.  
  ✅ *Example:*  
  Add new payment methods via new classes, not by editing `CheckoutService`.

- **Liskov Substitution Principle**  
  ➤ Subclasses must behave like the parent class.  
  ❌ *Bad:*  
  `Bird.fly()` breaks when called on a `Penguin`.  
  ✅ *Good:*  
  Split into `FlyingBird` and `NonFlyingBird`.

- **Interface Segregation Principle**  
  ➤ Prefer multiple small interfaces over one big one.  
  ✅ *Example:*  
  `Printable`, `Scannable`, not `OfficeMachine`.

- **Dependency Inversion Principle**  
  ➤ Depend on abstractions, not concretions.  
  ✅ *Example:*  
  Use `ILogger` interface so you can switch between `ConsoleLogger` and `FileLogger`.

- **Maximize Cohesion**  
  ➤ Keep related functionality together.  
  ✅ *Example:*  
  All order-related methods should be inside `OrderService`.

- **Hide Implementation Details**  
  ➤ Expose only what’s necessary.  
  ✅ *Example:*  
  Provide a `getBalance()` method; don’t let users access internal fields like `_transactions`.

- **Curly’s Law – Do One Thing Well**  
  ✅ *Example:*  
  A method should *only* send an email, not format the email and log it too.

- **Encapsulate What Changes**  
  ➤ Wrap volatile logic inside dedicated components.  
  ✅ *Example:*  
  Payment gateways change often — isolate in `PaymentProcessor`.

- **Command Query Separation (CQS)**  
  ➤ Methods should either modify state *or* return data — not both.  
  ✅ *Example:*  
  `updateUser()` → modifies,  
  `getUser()` → fetches

---

## ✅ Testing Principles

- **FIRST Testing**
  - **Fast** – Quick to run
  - **Independent** – Tests don’t rely on each other
  - **Repeatable** – Same results every time
  - **Self-validating** – Fail or pass without manual checking
  - **Timely** – Write tests while writing code

  ✅ *Example:*  
  Unit tests that cover one small function and don’t rely on DB.

- **Arrange, Act, Assert (AAA)**  
  ✅ *Example:*
  ```javascript
  // Arrange
  const calc = new Calculator();

  // Act
  const result = calc.add(2, 3);

  // Assert
  expect(result).toBe(5);
  ```

---

## 🎉 Outro

Thanks for watching! These principles help you write cleaner, easier-to-maintain code.

👉 **Like, Subscribe, and share** with your dev friends!  
👉 More content at: [semusings.dev](https://semusings.dev)  
👉 Subscribe: [youtube.com/@semusings](https://youtube.com/@semusings)

Until next time — **write less code, write better code!** 👋
