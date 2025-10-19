[Home](../index.md) | [Software Engineering and Design](./software-engineering.md) | [Databases](./databases.md) | [Final Integrated Improvements](./final-enhancements.md)

# Enhancement Two: Algorithms and Data Structures

## Artifact Overview

This artifact builds upon the Event Tracker application, enhanced in the previous artifact and refactored to **MVVM**. This artifact enhances the application by implementing a **dynamic search algorithm** that allows the user to filter and find specific events by searching for the event title. This artifact is included because it 
demonstrates my ability to design and integrate an efficient algorithmic solution to a real-world problem. 

---

## Event Tracker Dashboard with Filtered and Unfiltered Events

<img width="154" height="315" alt="image" src="https://github.com/user-attachments/assets/22539a25-eefd-4e58-b084-d22f39612ebe" />

<img width="152" height="314" alt="image" src="https://github.com/user-attachments/assets/85e7a893-082b-4666-8530-89696897cfbd" />

---

## Enhancement Implementation

This enhancement was made by modifying the `EventAdapter.java` class, which is responsible for managing the list of events that are displayed in the `RecyclerView`. 
The adapter originally maintained a single list of events, with the items in the list ordered by date and displayed in ascending order. 

To accommodate the search algorithm, the adapter was reworked to maintain two lists: one list, `events`, is the single source of truth that holds all existing events for the user, while another list, `displayedEvents`, contains the events that are actually displayed in the dashboard. When no search terms are entered, the displayed list is equal to the reference list. When a search term is entered, the search algorithm loops through the reference list and places any event with matching titles into the display list, whose contents are then shown in the dashboard. 

The algorithm has a **time complexity** of **O(N)**, meaning it performs a single pass through the list each time the search term changes. Given the application's scale and the number of events per user is expected to be relatively small, a linear-time algorithm is efficient and appropriate. 

---

## Course Outcomes Demonstrated

By designing and implementing the search algorithm, I met the course outcome I had planned to meet in Module One:

> "Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices."

---

## Reflection

While working on the enhancements, I faced challenges while trying to adapt the UI to the added functionalities, and I noticed that even small decisions during coding can have a significant impact on the behavior of the application and the user experience. 

---

## Links to Code
- [Original Code](https://github.com/atsh-omlet/EventTracker/tree/archive/original-state/app/src/main/java/com/cs360/eventtrackeratsushi)
- [Enhanced Code](https://github.com/atsh-omlet/EventTracker/tree/artifact2/app/src/main/java/com/cs360/eventtrackeratsushi)

---

[⬅ Back to Software Engineering and Design](./software-engineering.md) | [Next ➡ Databases](./database.md)
