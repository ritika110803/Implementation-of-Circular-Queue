C Program: Circular Queue Implementation Using Array

This project demonstrates how to implement a *Circular Queue* using an array in C.

Unlike a simple queue, a circular queue efficiently reuses empty spaces using modular arithmetic.

---

Description

The program:

* Implements a *Circular Queue* using a fixed-size array (MAX = 5)
* Uses front and rear pointers
* Performs:

  * *Enqueue (Insertion)*
  * *Dequeue (Deletion)*
  * *Display*
* Handles:

  * *Queue Overflow*
  * *Queue Underflow*
* Uses modulo (%) operation for circular behavior

This example is ideal for students learning *Circular Queues in Data Structures*.

---

Source Code

c

#include <stdio.h>

#include <stdlib.h>

#define MAX 5

int queue[MAX];
int front = -1;
int rear = -1;

// Enqueue operation

void enqueue(int value) {
   
    if ((rear + 1) % MAX == front) {
        printf("Queue Overflow! Cannot insert %d\n", value);
        return;
    }

    if (front == -1)  // First element
        front = 0;

    rear = (rear + 1) % MAX;
    queue[rear] = value;
    printf("%d inserted into queue\n", value);
}

// Dequeue operation

void dequeue() {
    
    
    if (front == -1) {
        printf("Queue Underflow! Queue is empty\n");
        return;
    }

    printf("%d removed from queue\n", queue[front]);

    if (front == rear) {
       
        // Queue becomes empty
       
        front = rear = -1;
    } else {
        front = (front + 1) % MAX;
    }
}

// Display queue

void display() {
    
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    printf("Queue elements are:\n");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear)
            break;
        i = (i + 1) % MAX;
    }
    printf("\n");
}

int main() {
   
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50);

    display();

    dequeue();
    dequeue();

    enqueue(60);
    enqueue(70);

    display();

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as circular_queue.c
2. Open terminal or command prompt
3. Compile the program:


gcc circular_queue.c -o circular_queue


4. Run the executable:


./circular_queue


(On Windows, use circular_queue.exe)

---

Sample Output


10 inserted into queue
20 inserted into queue
30 inserted into queue
40 inserted into queue
50 inserted into queue
Queue elements are:
10 20 30 40 50
10 removed from queue
20 removed from queue
60 inserted into queue
70 inserted into queue
Queue elements are:
30 40 50 60 70


---

Concepts Covered

* Circular Queue Data Structure
* FIFO (First In, First Out) principle
* Modulo arithmetic (%)
* Efficient space utilization
* Overflow and Underflow handling

---

How Circular Queue Works

In a circular queue:

* The queue wraps around when it reaches the end of the array.
* (rear + 1) % MAX determines the next position.
* Overflow condition:


(rear + 1) % MAX == front


This allows reusing freed space after dequeue operations.

---

Time Complexity

* *Enqueue:* O(1)
* *Dequeue:* O(1)
* *Display:* O(n)

---

Advantages Over Linear Queue

* Efficient memory usage
* Reuses empty slots
* Prevents wastage of array space

---

⚠️ Limitations

* Fixed maximum size (MAX = 5)
* Uses global variables

---
