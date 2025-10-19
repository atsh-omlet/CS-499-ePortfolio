[Home](../index.md) | [Software Engineering and Design](./software-engineering.md) | [Algorithms](./algorithms.md) | [Final Integrated Improvements](./final-enhancements.md)
# Enhancement Three: Databases

## Artifact Overview

This artifact enhances the Event Tracker application by migrating from **SQLite** for data storage to **MongoDB Realm**. This required modifying the data models and the `DatabaseHelper.java` class while keeping the existing app logic intact. This artifact is included because it demonstrates my ability to work with both traditional relational databases, as used in the original SQLite implementation, and modern NoSQL databases such as MongoDB Realm. 

---

## Enhancement Implementation

In the original implementation, the application used a single `Event` model class while the `DatabaseHelper` class constructed internal relational databases for user and event data. After migrating to Realm, I reconstructed the data layer by introducing separate `User` and `Event` model classes to work with Realm's **object-oriented data model**, which eliminates the need for explicit SQL queries, allowing data to be stored and retrieved directly as objects.

The migration involved several key steps:

- **Configured Realm:** Initialized Realm in `DatabaseHelper` with a schema including both `User` and `Event` classes.  
- **Redesigned data models:** Added primary key fields and Realm annotations (`@PrimaryKey`, `@Required`) to define schema and constraints.  
- **Refactored database operations:** Replaced all raw SQL queries and cursor management with Realm’s transaction API (`writeBlocking`).
- **Implemented data relationships:** Connected events to users through the `userId` field instead of maintaining foreign keys manually.

During this process, I encountered difficulties while working with the older Java-based Realm SDK and decided to use the newer Kotlin SDK. For this reason, the `DatabaseHelper` and model classes `Event` and `User` had to be written in Kotlin, while the rest of the application was written in Java. It was therefore paramount to maintain the original signature of the database to ensure smooth integration with the rest of the project.

Another important change I made was updating the architecture to use the **singleton pattern** for the database and repositories to improve consistency and resource management.

---

## Course Outcomes Demonstrated

By implementing MongoDB Realm and restructuring the data layer, I demonstrated the ability to apply modern database solutions and met the course outcome of:

> "Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals."

In addition, as I have been using Git consistently throughout development for version control, I have also met the course outcome of: 

> "Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts."

---

## Reflection

While improving the artifact, I gained valuable experience in database migration, the interoperability between Kotlin and Java, and object-based data modeling. I also realized how vitally important it is to enforce proper separation of concerns and modularity, since my earlier work in refactoring the application to MVVM architecture and decoupling the UI with database and business logic meant that I was able to completely overhaul the data layer of the application with minimal impact on the rest of the application. 

One major challenge I faced this week while working on the artifact was actually adding the Realm SDK and updating dependencies, as different versions supported different functionalities, and a slight mismatch between Gradle files would lead to catastrophic failure. Another challenge I faced was the app immediately crashing after startup, after having worked previously, which was caused by duplicate Realm file names and my configuration attempting to initiate multiple instances of the database with each startup.

---

## Links to Code
- [Original Code](https://github.com/atsh-omlet/EventTracker/tree/archive/original-state/app/src/main/java/com/cs360/eventtrackeratsushi)
- [Enhanced Code](https://github.com/atsh-omlet/EventTracker/tree/artifact3/app/src/main/java/com/cs360/eventtrackeratsushi)

---

[⬅ Back to Algorithms and Data Structures](./algorithms.md) | [Next ➡ Final Integrated Improvements ](./final-enhancements.md)
