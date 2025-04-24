---
marp: true
theme: semusings
paginate: true
header: '© Software Engineering Musings - <https://semusings.dev/> - subscribe us on :yt: 📺 at <https://youtube.com/@semusings> '
footer: ''
---

# Good Programming Principles
### (Simplified + Examples)

---

### 🎙️ Intro

Hey everyone! Welcome back to **Software Engineering Musings**!

Today we’re covering **Good Programming Principles** — simple rules that help you write clean, maintainable code.

👉 Don’t forget to **subscribe**: [youtube.com/@semusings](https://youtube.com/@semusings)  
👉 More content at: [semusings.dev](https://semusings.dev)

Let’s dive in 👇

---

## 💡 General Programming Principles

- **KISS – Keep It Simple, Stupid**  
  ➤ Don’t overthink it.  
  ✅ *Example:* Use `console.log()` instead of building a custom logger.

- **YAGNI – You Aren’t Gonna Need It**  
  ➤ Build only what you need right now.  
  ✅ *Example:* Don’t write a “search” feature unless users ask for it.

- **Do The Simplest Thing That Could Possibly Work**  
  ➤ Start with the basic solution.  
  ✅ *Example:* Hardcode values first, optimize later.

- **Separation of Concerns**  
  ➤ Keep different things separate.  
  ✅ *Example:* UI shouldn’t deal with file uploads.

- **Code For The Maintainer**  
  ➤ Write code like someone else will read it tomorrow.  
  ✅ *Example:* Use `userEmail` instead of `x`.

- **Avoid Premature Optimization**  
  ➤ Don’t try to make it fast before it works.  
  ✅ *Example:* Don’t use caching before knowing you need it.

- **Optimize for Deletion**  
  ➤ Code should be easy to remove.  
  ✅ *Example:* Don’t spread logic across 10 files if one is enough.

- **DRY – Don’t Repeat Yourself**  
  ➤ Reuse instead of copy-pasting.  
  ✅ *Example:* Use a common validator for all forms.

- **Boy Scout Rule**  
  ➤ Leave the code better than you found it.  
  ✅ *Example:* Rename unclear variables when you touch a file.

---

## 🔗 Relationships Between Code Components

- **Connascence**  
  ➤ If changing A always breaks B, that’s bad.  
  ✅ *Example:* Two tightly-coupled modules needing renames together.

- **Minimize Coupling**  
  ➤ Reduce how much parts depend on each other.  
  ✅ *Example:* Pass props to a component instead of letting it fetch data.

- **Law of Demeter**  
  ➤ Talk only to direct friends.  
  ✅ *Bad:* `user.getProfile().getAvatar().getUrl()`  
  ✅ *Good:* `user.getAvatarUrl()`

- **Composition Over Inheritance**  
  ➤ Prefer building from smaller parts.  
  ✅ *Example:* Use a `CanFly` trait for a `Fish` instead of extending `Bird`.

- **Orthogonality**  
  ➤ Changing one thing shouldn’t break another.  
  ✅ *Example:* Switching DB drivers shouldn’t affect UI.

- **Robustness Principle**  
  ➤ Be strict in what you send, flexible in what you receive.  
  ✅ *Example:* Don’t crash on extra JSON fields.

- **Inversion of Control**  
  ➤ Let the framework drive, not hard-coded logic.  
  ✅ *Example:* Inject services instead of new-ing them up.

---

## 🧱 Inside Classes and Modules

- **Single Responsibility Principle**  
  ➤ One job per module/class.  
  ✅ *Example:* Don't log emails and send emails in one class.

- **Open/Closed Principle**  
  ➤ Open to extension, closed to modification.  
  ✅ *Example:* Use strategy pattern for new payment methods.

- **Liskov Substitution Principle**  
  ➤ Subclasses should work like their parents.  
  ❌ *Bad:* `Penguin` breaks `Bird.fly()`  
  ✅ *Good:* Use different abstractions.

- **Interface Segregation Principle**  
  ➤ Don’t force unused methods.  
  ✅ *Example:* Small interfaces like `ICanFly`, `ICanSwim`

- **Dependency Inversion Principle**  
  ➤ Depend on interfaces, not details.  
  ✅ *Example:* Inject an `EmailService` instead of creating it inside.

- **Maximize Cohesion**  
  ➤ Keep related code together.  
  ✅ *Example:* All order logic in one class.

- **Hide Implementation Details**  
  ➤ Show what’s needed, hide the rest.  
  ✅ *Example:* `getName()` exposes full name, internals stay hidden.

- **Curly’s Law – Do One Thing Well**  
  ✅ *Example:* A function should only sort data, not save it too.

- **Encapsulate What Changes**  
  ➤ Keep changeable logic in one place.  
  ✅ *Example:* Isolate payment logic.

- **Command Query Separation**  
  ➤ Methods should *either* do something *or* return something.  
  ✅ *Example:* `createUser()` creates, `getUser()` fetches.

---

## ✅ Testing Principles

- **FIRST Principles of Testing:**
  - **Fast**
  - **Independent**
  - **Repeatable**
  - **Self-validating**
  - **Timely**  
    ✅ *Example:* Tests should be written along with the code.

- **Arrange, Act, Assert Pattern**  
  ✅ *Example (JS):*
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
