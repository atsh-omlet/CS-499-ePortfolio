[Home](../index.md) | [Algorithms](./algorithms.md) | [Databases](./databases.md) | [Final Integrated Improvements](./final-enhancements.md)

# Enhancement One: Software Engineering and Design

## Artifact Overview
For the CS 499 Capstone Project, I decided to use my CS 360 final project, which is an event tracker application. The app was originally designed with the following functionalities: 
- Allow for user login/logout
- Add events to the dashboard
- Edit/delete events from the dashboard
- Receive SMS notifications for upcoming events
  
For my Capstone Project, I will be enhancing this application in the three relevant categories. For Enhancement One, I will improve the architecture of the application. This artifact is included in my capstone as it demonstrates my ability to create
working software and my improved understanding of best practices in software design. 

Specifically, I refactored the application from an **MVC-based architecture** to an **MVVM-based** architecture. Further, I also introduced **password hashing** to improve security.

---

## Original Architecture
Originally, the Event Tracker used an **MVC-like** design. In this structure, the `MainActivity.java` class, for example, which managed the UI for the login screen, also handled business logic such as user authentication and had direct access to the database 
(`DatabaseHelper.java`).

This severely violated the principle of the separation of concerns, which is the idea that code should be broken up into distinct components where each component manages a specific function (Namov, 2020). 
As a result, the code was difficult to read, maintain, and reuse.

---

## Enhancement Implementation
To address these issues, I **decoupled the business logic** from the Activity classes and

- Consolidated data operations into a new **repository class** (`UserRepository.java`) to abstract database operations.
- Added a **SessionManager.java** class for managing shared preferences.
- Added a **SecurityUtils.java** class for password hashing.
- Introduced View Models such as **LoginViewModel.java**, which connects the repository layer to the UI and exposes **LiveData** such as login status and error messages.

Essentially, the database handles CRUD operations, which are abstracted by the repositories for the rest of the application. Business logic is moved out from Activity classes and into View Models, which interact with repositories and additional utility classes to expose data to the UI via `Live Data`. This design allows **Activity classes** like `MainActivity.java` and `CreateLoginActivity.java` to focus entirely on UI and observe data changes instead of directly managing authentication or database access, enforcing the principle of separation of concerns. 

---

## Course Outcomes Demonstrated
In Module One, I planned to meet the following course outcome:
> "Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources"

By refactoring the user-related functionalities to adhere to **MVVM architecture** and by implementing password hashing, I have been able to meet this outcome, in addition to:

> “Use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals.”

---

## Reflection
Through this enhancement, I gained a deeper appreciation for **clean architecture**.  
As I refactored to MVVM, I realized how messy my original design had been and how separating concerns greatly improved readability and maintainability.

I also became more familiar with **Android components** like `ViewModel` and `LiveData`, though I need more practice to become fully proficient.

One main challenge was restructuring the application without breaking it, since the Activities were tightly coupled to business logic. 

## Links to Code
- [Original Code](https://github.com/atsh-omlet/EventTracker/tree/archive/original-state/app/src/main/java/com/cs360/eventtrackeratsushi)
- [Enhanced Code](https://github.com/atsh-omlet/EventTracker/tree/artifact1/app/src/main/java/com/cs360/eventtrackeratsushi)

---

## References
Naumov, A. (2020, January 16). *Separation of Concerns in Software Design.* GitHub. [https://nalexn.github.io/separation-of-concerns/](https://nalexn.github.io/separation-of-concerns/)

---

[⬅ Back to Home](../index.md) | [Next ➡ Algorithms and Data Structures](./algorithms.md)
