Here's a code implementation of a [[Linked List]] in C++.

```cpp
#include <iostream>

using namespace std;

struct Node{
    Node *next;
    int val;
} typedef Node;

void traversal(Node *head)
{
    while (head != NULL){
        cout << head->val << " -> ";
        head = head->next;
    }
    cout << "NULL" << '\n';
}

void insertAtEnd(Node **headRef, int value){
    Node *newNode = new Node; // same as (Node *)malloc(sizeof(Node))
    Node *last = *headRef;

    newNode->val = value;
    newNode->next = NULL;

    if (*headRef == NULL){
        *headRef = newNode;
        return;
    }

    while (last->next != NULL){
        last = last->next;
    }

    last->next = newNode;
}

void insertAtBegin(Node **headRef, int value){
    Node *newNode = new Node;

    newNode->val = value;

    if (*headRef == NULL){
        newNode->next = NULL;
        *headRef = newNode;
        return;
    }

    newNode->next = *headRef;
    *headRef = newNode;
}

void insertAfter(Node* prev_node, int value){
    
    if(prev_node == NULL){
        cout << "ALERT: PREV NODE CAN'T BE NULL" << '\n';
        return;
    }
    
    Node* newNode = new Node;
    newNode->val = value;
    newNode->next = prev_node->next;
    prev_node->next = newNode;
}

Node* getNode(Node* headRef, int val){
    while(headRef != NULL){
        if(headRef->val == val)
            return headRef;
        headRef = headRef->next;
    }
    cout << "ALERT: NODE NOT FOUND" << '\n';
    return NULL;
}

int main(){
    Node *head = NULL;

    insertAtEnd(&head, 20);
    insertAtEnd(&head, 30);
    insertAtEnd(&head, 40);
    insertAtBegin(&head, 50);
    insertAtBegin(&head, 60);

    Node *example = getNode(head, 30);
    cout << example->val << '\n';
    traversal(head);

    insertAfter(example, 100);
    traversal(head);
}
```

# Commentary

In this section we'll be discussing about each function in the code above (stay with me until the end, there's good advice down there). 

## Traversal

The most basic function in the code. I pass the pointer to the first node in the list to keep its reference. While the reference is not null, I print the value contained in it and advance to the next node.

## Insert at end

I start by creating the node that is going to enter the list.

Then I check if the head is null. If it is, then the inserted element will be the first one so I assign it to the head of my linked list.

Otherwise, I do a traversal of the list until I get to the last element, then I assign the new node as the new last element.

## Insert at begin

I start by creating the node that is going to enter the list.

If the head is null, then I assign the new node to the head of the linked list.

Otherwise, I assign the current head to the 'next' slot of my new node, then I in fact make it the new head of the linked list.

## Insert after

This one is pretty basic, I just check if the node passed by parameter is a null pointer (because a null pointer doesn't have a next slot, so it would not only be conceptually wrong but would also crash the code), then if not I create the new node and assign it as the next node to the node I passed via parameter.

## Get node

Basically a traversal in which, instead of printing, I search for the first node in my linked list which contains the value given as parameter and then return it.

## Extra: hardships I went through while studying this

The hardest concept to deal with while learning all of this was BY FAR the pointers. Why do I need to use double pointers on this function? If I need to use it on this one, why I don't need to use on this other one? It's a pain in the ass, I'm not gonna lie. So I'm leaving little things I learned here in hopes of saving someone from going through all of this as well.

- When passing things as parameters, we create a copy of them to the function, not the things themselves.
- Using single pointers are mostly done so we can modify a content inside the node. By passing the address to the node itself, it's possible to change its content, because we have a copy of the original address to the node itself.
- Using double pointers are mostly done so we can modify an address for it to point somewhere else. For example, in the functions [[#Insert at end]] and [[#Insert at begin]], there's the possibility of changing which node will represent the head of the linked list. You can think of it as a capsule that can be used so you can alter the address of the node inside the function. Head once pointed to node X, and after the function will point to node Y. Simple as that.
