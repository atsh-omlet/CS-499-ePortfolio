[Home](../index.md) | [Software Engineering and Design](./software-engineering.md) | [Algorithms](./algorithms.md) | [Databases](./databases.md)
# Final Integrated Improvements

## Dynamic Header
Previously, all events were displayed in the dashboard consecutively. This made it difficult to differentiate between events from different dates. To resolve this, I implemented an algorithm in the `EventAdapter` to iterate over events in the `displayedItem` list and insert a header before an event if its date is different from the preceding event. This process is executed each time the `displayedItem` list is reconstructed, ensuring the headers are inserted dynamically as the dashboard updates.

<img width="152" height="328" alt="image" src="https://github.com/user-attachments/assets/8de231d4-32e3-4db7-b1a1-62fd6fb0442e" />


---

## Filtering by Date

Similar to how the search algorithm is implemented in Enhancement Two, I added an algorithm that filters events by date entered in the format of `yyyy mm dd`. By normalizing the input, the algorithm can accept user input formatted either with '-', '/', or ' ', as well as ignore trailing symbols. This algorithm also has a time complexity of **O(N)**. 

---

## Notifications Scheduling and Permissions

A `NotificationHelper` class was added to schedule and cancel notifications by scheduling exact alarms. Notifications are handled after a notification channel is constructed by the `NotificationReceiver` class. A `BootReciever` was implemented to reschedule notifications in the event of a reboot. Since scheduling exact alarms requires explicit permissions above **Android API level 31**, modifications were made to the `DashboardViewModel` and `DashboardActivity` classes to request user permission. 

---

## Additional Enhancements

Further enhancements include adding an app icon, making modifications to the dashboard appearance, and improving the file structure of the project. The newest version of the Event Tracker application, after all capstone enhancements and further improvements, can be found here:

[View Final Application](https://github.com/atsh-omlet/EventTracker/tree/main/app/src/main/java/com/cs360/eventtrackeratsushi)

---


[⬅ Back Databases](./databases.md) | [Back to Home ➡ ](../index.md)
