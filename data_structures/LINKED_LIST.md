# Linked List

<!-- TOC -->
* [Linked List](#linked-list)
  * [Types of linked lists](#types-of-linked-lists)
    * [Single-linked list](#single-linked-list)
    * [Double linked list](#double-linked-list)
    * [Circular linked list](#circular-linked-list)
  * [Operations on Linked Lists](#operations-on-linked-lists)
  * [Advantages of Linked Lists](#advantages-of-linked-lists)
  * [Disadvantages of Linked Lists](#disadvantages-of-linked-lists)
  * [Common Problems](#common-problems)
    * [Finding the middle element in a Linked list](#finding-the-middle-element-in-a-linked-list)
    * [Reverse a Linked list](#reverse-a-linked-list)
    * [Rotate a Linked List](#rotate-a-linked-list)
    * [Reverse a Linked List in groups of given size](#reverse-a-linked-list-in-groups-of-given-size)
    * [Intersection point in Y shaped Linked lists](#intersection-point-in-y-shaped-linked-lists)
    * [Detect Loop in Linked list](#detect-loop-in-linked-list)
    * [Remove loop in Linked List](#remove-loop-in-linked-list)
    * [n’th node from end of Linked list](#nth-node-from-end-of-linked-list)
    * [Flattening a Linked List](#flattening-a-linked-list)
    * [Merge two sorted Linked lists](#merge-two-sorted-linked-lists)
    * [Pairwise swap of a Linked list](#pairwise-swap-of-a-linked-list)
    * [Add two numbers represented by Linked lists](#add-two-numbers-represented-by-linked-lists)
    * [Check if Linked List is Palindrome](#check-if-linked-list-is-palindrome)
    * [Implement Queue using Linked List](#implement-queue-using-linked-list)
    * [Implement Stack using Linked List](#implement-stack-using-linked-list)
    * [Given a Linked list of 0s, 1s and 2s, sort it](#given-a-linked-list-of-0s-1s-and-2s-sort-it)
    * [Delete without head pointer](#delete-without-head-pointer)
    * [Merge Sort for Linked Lists](#merge-sort-for-linked-lists)
<!-- TOC -->

A linked list is a linear data structure, in which the elements are not stored at contiguous memory locations. The 
elements in a linked list are linked using pointers as shown in the below image:

![linked list](../src/linked_list.png)

## Types of linked lists

### Single-linked list

In a singly linked list, each node contains a reference to the next node in the sequence. Traversing a singly linked 
list is done in a forward direction.

![single linked list](../src/single-linked-list.png)


```python
# Node class 
class Node: 

    # Function to initialize the node object 
    def __init__(self, data): 
        self.data = data # Assign data 
        self.next = None # Initialize next as null 

# Linked List class 
class LinkedList: 

    # Function to initialize the Linked List object 
    def __init__(self): 
        self.head = None
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
     def __init__(self):
         self.head = None
         
     def add_node(self, data):
         new_node = Node(data)
         new_node.next = self.head
         if self.head is not None:
             self.head.prev = new_node
             self.head = new_node
```

### Double linked list

In a doubly linked list, each node contains references to both the next and previous nodes. This allows for traversal 
in both forward and backward directions, but it requires additional memory for the backward reference.

![double linked list](../src/double-linked-list.png)

```python
# Node of a doubly linked list 
class Node: 
    def __init__(self, next=None, prev=None, data=None): 
        self.next = next # reference to next node in DLL 
        self.prev = prev # reference to previous node in DLL 
        self.data = data
```

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

class DoublyLinkedList:
    def __init__(self):
        self.head = None
        
    def add_node(self, data):
        new_node = Node(data)
        new_node.next = self.head
        if self.head is not None:
            self.head.prev = new_node
            self.head = new_node
```

### Circular linked list

 In a circular linked list, the last node points back to the head node, creating a circular structure. It can be either 
 singly or doubly linked.

![circular linked list](../src/circular-linked-list.png)

## Operations on Linked Lists

- *Insertion*: Adding a new node to a linked list involves adjusting the pointers of the existing nodes to maintain the 
proper sequence. Insertion can be performed at the beginning, end, or any position within the list
- *Deletion*: Removing a node from a linked list requires adjusting the pointers of the neighboring nodes to bridge the 
gap left by the deleted node. Deletion can be performed at the beginning, end, or any position within the list.
- *Searching*: Searching for a specific value in a linked list involves traversing the list from the head node until the 
value is found or the end of the list is reached.

## Advantages of Linked Lists
- Dynamic nature: Linked lists are used for dynamic memory allocation.
- Memory efficient: Memory consumption of a linked list is efficient as its size can grow or shrink dynamically according 
to our requirements, which means effective memory utilization hence, no memory wastage.
- Ease of Insertion and Deletion: Insertion and deletion of nodes are easily implemented in a linked list at any 
position.
- Implementation: For the implementation of stacks and queues and for the representation of trees and graphs.
- The linked list can be expanded in constant time.

## Disadvantages of Linked Lists
- Memory usage: The use of pointers is more in linked lists hence, complex and requires more memory.
- Accessing a node: Random access is not possible due to dynamic memory allocation.
- Search operation costly: Searching for an element is costly and requires O(n) time complexity.
- Traversing in reverse order: Traversing is more time-consuming and reverse traversing is not possible in singly linked
lists. 

## Common Problems

### Finding the middle element in a Linked list
### Reverse a Linked list
### Rotate a Linked List
### Reverse a Linked List in groups of given size
### Intersection point in Y shaped Linked lists
### Detect Loop in Linked list
### Remove loop in Linked List
### n’th node from end of Linked list
### Flattening a Linked List
### Merge two sorted Linked lists
### Pairwise swap of a Linked list
### Add two numbers represented by Linked lists
### Check if Linked List is Palindrome
### Implement Queue using Linked List
### Implement Stack using Linked List
### Given a Linked list of 0s, 1s and 2s, sort it
### Delete without head pointer
### Merge Sort for Linked Lists