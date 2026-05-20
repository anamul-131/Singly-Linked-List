# Singly-Linked-List
Academic Practice 

/* a singly linked list containing the elements 30, 40, 50, and 60. Insert 70 in the middle of the list, delete the node containing 60, and finally insert 20 at the beginning of the linked list */


#include <stdio.h>
#include <stdlib.h>
// Creating node structure
struct Node {
    int data;
    struct Node* next;
};

// Function to create new node
struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;
    return newNode;
}
// Function to print linked list

void displayList(struct Node* head) {
    struct Node* temp = head;

    printf("Linked List: ");

    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }

    printf("\n");
}

int main() {

    // Initial linked list: 30 40 50 60
    struct Node* head = createNode(30);
    head->next = createNode(40);
    head->next->next = createNode(50);
    head->next->next->next = createNode(60);

    printf("Original ");
    displayList(head);

    // Insert 70 in the middle (after 40)
    struct Node* newNode = createNode(70);

    newNode->next = head->next->next;
    head->next->next = newNode;

    printf("After inserting 70 in middle ");
    displayList(head);

    // Delete 60
    struct Node* temp = head;

    while (temp->next != NULL && temp->next->data != 60) {
        temp = temp->next;
    }

    if (temp->next != NULL) {
        struct Node* deleteNode = temp->next;
        temp->next = temp->next->next;
        free(deleteNode);
    }

    printf("After deleting 60 ");
    displayList(head);

    // Insert 20 at beginning
    struct Node* beginNode = createNode(20);
    beginNode->next = head;
    head = beginNode;

    printf("After inserting 20 at beginning ");
    displayList(head);
    return 0;
}
