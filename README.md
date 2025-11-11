# DSA-MINI-PROJECT

Hospital Emergency Room Management System Manage patients based on severity (priority). Highest severity gets immediate service. Use Heap (Priority Queue)


# 🏥 Hospital Emergency Room Management System

## 📘 Overview

The **Hospital Emergency Room Management System** is a C-based console program that manages patients according to their **severity level** using a **max-heap (priority queue)**.
Patients with higher severity receive **immediate service**, simulating a real-world hospital triage system.

This system ensures that:

* The most critical patients are served first.
* Patients with the same severity are served in order of arrival.
* Staff can easily **add**, **serve**, or **view** patients currently waiting.

---

## ⚙️ Features

✅ Add new patients with their name, age, and severity level (1–10)
✅ Automatically prioritizes patients using a **max-heap**
✅ Serves the most severe patient first
✅ Maintains order for patients with equal severity (earlier arrival first)
✅ Displays the current queue of patients
✅ Input validation for safer and user-friendly operation

---

## 🧮 Data Structure Used

The system uses a **Binary Max-Heap** to maintain the patient queue.

* **Heap Property:**
  Each node’s severity is higher than or equal to that of its children.
* **Insertion:** O(log n)
* **Serving (removal):** O(log n)
* **Display:** O(n)

Patients are compared by:

1. **Severity (higher first)**
2. **Arrival order (earlier first)** if severities are equal

---

## 🧠 Logic Flow

1. **Add Patient** → Insert into heap → Reheap Up
2. **Serve Patient** → Remove root (max priority) → Reheap Down
3. **Display Patients** → Traverse heap and show queue
4. **Exit** → Safely terminate program

---

## 🧾 Sample Interaction

```
--- Hospital Emergency Room Management ---
1. Add Patient
2. Serve Patient
3. Display Patients
4. Exit
Enter your choice: 1
Enter name: Ramesh
Enter age: 45
Enter severity (1-10): 9
Patient 'Ramesh' added (age 45, severity 9).

Enter your choice: 1
Enter name: Priya
Enter age: 30
Enter severity (1-10): 10
Patient 'Priya' added (age 30, severity 10).

Enter your choice: 3
--- Current Patient Queue (heap order) ---
1) Name: Priya | Age: 30 | Severity: 10 | Arrival: 1
2) Name: Ramesh | Age: 45 | Severity: 9 | Arrival: 0

Enter your choice: 2
Serving patient: Priya | Age: 30 | Severity: 10

Enter your choice: 4
Exiting system. Goodbye!
```

---

## 👨‍💻 Author

Darshan Puranik
Second Year B.E. (Electronics & Telecommunication)
Savitribai Phule Pune University (SPPU)
