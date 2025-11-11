# DSA-MINI-PROJECT
Hospital Emergency Room Management System Manage patients based on severity (priority). Highest severity gets immediate service. Use Heap (Priority Queue)
#include <stdio.h>
#include <string.h>

#define MAX 100  /* Maximum number of patients */

/* Structure to represent a patient */
struct Patient {
    char name[50];
    int age;
    int severity; /* Higher number = higher priority */
};

struct Patient heap[MAX];
int heapSize = 0;

/* Function to swap two patients */
void swap(struct Patient *a, struct Patient *b) {
    struct Patient temp = *a;
    *a = *b;
    *b = temp;
}

/* Function to insert a new patient into the heap */
void insertPatient(char name[], int age, int severity) {
    int i;
    heapSize++;
    i = heapSize - 1;
    strcpy(heap[i].name, name);
    heap[i].age = age;
    heap[i].severity = severity;

    /* Reheap Up to maintain max-heap property */
    while (i != 0 && heap[(i - 1) / 2].severity < heap[i].severity) {
        swap(&heap[i], &heap[(i - 1) / 2]);
        i = (i - 1) / 2;
    }
}

/* Function to heapify (reheap down) */
void heapify(int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && heap[left].severity > heap[largest].severity)
        largest = left;

    if (right < n && heap[right].severity > heap[largest].severity)
        largest = right;

    if (largest != i) {
        swap(&heap[i], &heap[largest]);
        heapify(n, largest);
    }
}

/* Function to serve the patient with highest priority */
void servePatient() {
    if (heapSize <= 0) {
        printf("\nNo patients to serve.\n");
        return;
    }

    printf("\nServing patient: %s (Severity: %d)\n", heap[0].name, heap[0].severity);

    heap[0] = heap[heapSize - 1];
    heapSize--;
    heapify(heapSize, 0);
}

/* Function to display all patients */
void displayPatients() {
    int i;
    if (heapSize == 0) {
        printf("\nNo patients in the queue.\n");
        return;
    }

    printf("\n--- Current Patient Queue (by severity) ---\n");
    for (i = 0; i < heapSize; i++) {
        printf("Name: %s | Age: %d | Severity: %d\n", heap[i].name, heap[i].age, heap[i].severity);
    }
}

/* Main function */
int main() {
    int choice;
    char name[50];
    int age, severity;

    while (1) {
        printf("\n--- Hospital Emergency Room Management ---\n");
        printf("1. Add Patient\n");
        printf("2. Serve Patient\n");
        printf("3. Display Patients\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 1) {
            printf("Enter name: ");
            scanf("%s", name);
            printf("Enter age: ");
            scanf("%d", &age);
            printf("Enter severity (1-10): ");
            scanf("%d", &severity);
            insertPatient(name, age, severity);
        }
        else if (choice == 2) {
            servePatient();
        }
        else if (choice == 3) {
            displayPatients();
        }
        else if (choice == 4) {
            printf("\nExiting system. Goodbye!\n");
            break;
        }
        else {
            printf("\nInvalid choice. Try again.\n");
        }
    }

    return 0;
}
