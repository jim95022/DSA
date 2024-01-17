<!-- TOC -->
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

```text
Given a singly linked list of N nodes.
The task is to find the middle of the linked list. For example, if the linked list is
1 -> 2 -> 3 -> 4 -> 5, then the middle node of the list is 3.
If there are two middle nodes(in case, when N is even), print the second middle element.
For example, if the linked list given is 1->2->3->4->5->6, then the middle node of the list is 4.

Input:
LinkedList: 1 -> 2 -> 3 -> 4 -> 5
Output: 3 
Explanation: 
Middle of linked list is 3.

Input:
LinkedList: 2 -> 4 -> 6 -> 7 -> 5 -> 1
Output: 7 
Explanation: 
Middle of linked list is 7.

Your Task:
The task is to complete the function getMiddle() which takes a head reference as the only argument and should return the 
data at the middle node of the linked list.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(1).

Constraints:
1 <= N <= 5000
```

```python
class Solution:
    #  Should return data of middle node. If linked list is empty, then  -1
    def findMid(self, head):
        
        if not head:
            return -1
        
        need_to_move_middle_node = True
        current_node = head
        middle_node = head
        
        while True:
            
            if current_node.next:
                current_node = current_node.next
            else:
                return middle_node.data
            
            if need_to_move_middle_node:
                middle_node = middle_node.next
            
            need_to_move_middle_node = not need_to_move_middle_node
```

```python
class Solution:
    def findMid(self, head):
        
        if not head:
            return -1
    
        middle_node = head
        current_node = head
        
        while current_node and current_node.next:
            middle_node = middle_node.next
            # this pointer moves 1 nodes ahead everytime loop is run
        
            current_node = current_node.next.next
            # this pointer moves 2 nodes ahead everytime loop is run
        
        return middle_node.data
        # since slow was moving with half speed, it is there at halfway point
```

### Reverse a Linked list

```text
Given a linked list of N nodes. The task is to reverse this list.

Example 1:

Input:
LinkedList: 1->2->3->4->5->6
Output: 6 5 4 3 2 1
Explanation: After reversing the list, 
elements are 6->5->4->3->2->1.
Example 2:

Input:
LinkedList: 2->7->8->9->10
Output: 10 9 8 7 2
Explanation: After reversing the list,
elements are 10->9->8->7->2.
Your Task:
The task is to complete the function reverseList() with head reference as the only argument and should return new head after reversing the list.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(1).

Constraints:
1 <= N <= 104
```

```python
class Solution:
    #Function to reverse a linked list.
    def reverseList(self, head):

        new_head = None

        while head:
            helper_node = head.next  # 2 3 4 ...   # 3 4 5 ...
            head.next = new_head     # None        # 1 None ...
            new_head = head          # 1 None ...  # 2 1 None ...
            head = helper_node       # 2 3 4 ...   # 3 4 5 ...

        return new_head
```

```python
class Solution:
    #Function to reverse a linked list.
    def reverseList(self, head):
        if head is None:
            return None
        
        #taking three pointers to store the current, previous and next nodes.
        prev = None
        current = head
        next = current.next
        
        
        while current is not None:
            #taking the next node as next.
            next = current.next 
            
            #storing the previous node in link part of current node.
            current.next = prev 
            
            #updating prev from previous node to current node.
            prev = current
            
            #updating current node to next node.
            current = next           
        
        return prev
```

### Rotate a Linked List

```text
Given a singly linked list of size N. The task is to left-shift the linked list by k nodes, where k is a given positive 
integer smaller than or equal to length of the linked list.

Example 1:

Input:
N = 5
value[] = {2, 4, 7, 8, 9}
k = 3
Output: 8 9 2 4 7
Explanation:
Rotate 1: 4 -> 7 -> 8 -> 9 -> 2
Rotate 2: 7 -> 8 -> 9 -> 2 -> 4
Rotate 3: 8 -> 9 -> 2 -> 4 -> 7
Example 2:

Input:
N = 8
value[] = {1, 2, 3, 4, 5, 6, 7, 8}
k = 4
Output: 5 6 7 8 1 2 3 4

Your Task:
You don't need to read input or print anything. Your task is to complete the function rotate() which takes a head 
reference as the first argument and k as the second argument, and returns the head of the rotated linked list.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(1).

Constraints:
1 <= N <= 103
1 <= k <= N
```

```python
    def rotate(self, head, k):

        current_node = None
        left_part = head

        for _ in range(k):
            if left_part.next:
                current_node = left_part
                left_part = left_part.next
            else:
                return head

        current_node.next = None

        new_head = left_part

        while left_part.next:
            left_part = left_part.next

        left_part.next = head

        return new_head
```

```python
class Solution:
    
    #Function to rotate a linked list.
    def rotate(self, head, k):
        if k == 0:
            return head
        
        walk = head     # 1 2 3 ...
        prev = None     # None
        
        
        #this loop runs k times and walk pointer moves k nodes ahead 
        #and reaches new head node.
        for _ in range(k):
            prev = walk          # 1 2 3 ... # 2 3 4 ... # 3 4 5 ...
            walk = walk.next     # 2 3 4 ... # 3 4 5 ... # 4 5 6
            
            #considering cases where k>=n so nothing needs to be done.
            if walk is None:
                return head
        
        #we store the walk pointer which gives the first node in newHead.
        newHead = walk          # 4 5 6
        
        #since prev points to the node placed before new head it is new tail
        #or the last node of new list so we store null in it's link part.
        prev.next = None        # 3 None
        
        #we keep moving the walk pointer till we reach the last node of list.
        while walk.next is not None:
            walk = walk.next   # 4 5 6  # 5 6  # 6
        
        #connecting last node of old list to old head.
        walk.next = head       # 6 1 2 ...
        
        #returning the new list.
        return newHead         # 4 5 6
```

### Reverse a Linked List in groups of given size

```text
Given a linked list of size N. The task is to reverse every k nodes (where k is an input to the function) in the linked 
list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should be considered as a group and
 must be reversed (See Example 2 for clarification).

Example 1:

Input:
LinkedList: 1 -> 2 -> 2 -> 4 -> 5 -> 6 -> 7 -> 8
K = 4
Output: 4 2 2 1 8 7 6 5 
Explanation: 
The first 4 elements 1,2,2,4 are reversed first 
and then the next 4 elements 5,6,7,8. Hence, the 
resultant linked list is 4->2->2->1->8->7->6->5.
Example 2:

Input:
LinkedList: 1 -> 2 -> 3 -> 4 -> 5
K = 3
Output: 3 2 1 5 4 
Explanation: 
The first 3 elements are 1,2,3 are reversed 
first and then elements 4,5 are reversed.Hence, 
the resultant linked list is 3->2->1->5->4.
Your Task:
You don't need to read input or print anything. Your task is to complete the function reverse() which should reverse the
 linked list in group of size k and return the head of the modified linked list.

Expected Time Complexity : O(N)
Expected Auxilliary Space : O(1)

Constraints:
1 <= N <= 105
1 <= k <= N
```

```python
class Solution:
    def reverse(self,head, k):
        current_node = head
        new_head = None
        count = 0

        while current_node and count != k:
            temp_node = current_node.next
            current_node.next = new_head
            new_head = current_node
            current_node = temp_node
            count += 1

        if temp_node:
            head.next = self.reverse(temp_node, k)

        return new_head
```

```python
class Solution:
    def reverse(self, head, k):
        current = head
        next = None
        prev = None
        count = 0
        
        while (current is not None and count < k):
            # reversing k elements
            next = current.next              # storing value of next node
            current.next = prev              # reversing link
            prev = current                   # updating prev
            current = next                   # updating current
            count += 1
        
        if next is not None:    # checking if there are more nodes ahead
            head.next = self.reverse(next, k)     # reversing those recursively
        
        return prev
```

### Intersection point in Y shaped Linked lists

```text
Given two singly linked lists of size N and M, write a program to get the point where two linked lists intersect each other.

Example 1:

Input:
LinkList1 = 3->6->9->common
LinkList2 = 10->common
common = 15->30->NULL
Output: 15
Explanation:
Y ShapedLinked List
Example 2:

Input: 
Linked List 1 = 4->1->common
Linked List 2 = 5->6->1->common
common = 8->4->5->NULL
Output: 8
Explanation: 

4              5
|              |
1              6
 \             /
  8   -----  1 
   |
   4
   |
  5
  |
  NULL       
Your Task:
You don't need to read input or print anything. The task is to complete the function intersectPoint() which takes the pointer to the head of linklist1(head1) and linklist2(head2) as input parameters and returns data value of a node where two linked lists intersect. If linked list do not merge at any point, then it should return -1.
Challenge : Try to solve the problem without using any extra space.

 

Expected Time Complexity: O(N+M)
Expected Auxiliary Space: O(1)

 

Constraints:
Length of Both linkedList before intersection(if any) is greater than 0.
2 ≤ N + M ≤ 2*105
-1000 ≤ value ≤ 1000
```

```python
#Function to find intersection point in Y shaped Linked Lists.
def intersetPoint(head1,head2):
            
    head1_len = 0
    head2_len = 0

    current_head = head1

    while current_head:
        current_head = current_head.next
        head1_len += 1

    current_head = head2

    while current_head:
        current_head = current_head.next
        head2_len += 1

    if head1_len > head2_len:
        for _ in range(head1_len - head2_len):
            head1 = head1.next
    else:
        for _ in range(head2_len - head1_len):
            head2 = head2.next

    while head1.next and head2.next:
        if head1.next == head2.next:
            return head1.next.data
        head1 = head1.next
        head2 = head2.next

    return -1
```

```python
def getSize(head):
    ret = 0
    while head is not None:
        head = head.next
        ret+=1
    return ret

#Function to find intersection point in Y shaped Linked Lists.
def intersetPoint(head1,head2):
    
    #finding length of list1.
    n1 = getSize(head1)
    
    #finding length of list2.
    n2 = getSize(head2)
    
    #if list1 is longer, we ignore some of its starting
    #elements till it has as many elements as list2.
    while n1>n2:
        head1 = head1.next
        n1-=1
    
    #similarly, if list2 is longer, we ignore some of its starting
    #elements till it has as many elements as list1.
    while n2>n1:
        head2 = head2.next
        n2-=1
    
    
    #now we simply traverse ahead till we get the intersection point, if there 
    #is none, this loop will break when both pointers point at NULL.
    while head1 != head2:
        head1 = head1.next
        head2 = head2.next

    # if head1 is not NULL, we return its data otherwise we return -1.
    if head1 is not None:
        return head1.data
    return -1
```

### Detect Loop in Linked list

```text
Given a linked list of N nodes. The task is to check if the linked list has a loop. Linked list can contain self loop.

Example 1:

Input:
N = 3
value[] = {1,3,4}
x(position at which tail is connected) = 2
Output: True
Explanation: In above test case N = 3.
The linked list with nodes N = 3 is
given. Then value of x=2 is given which
means last node is connected with xth
node of linked list. Therefore, there
exists a loop.
Example 2:

Input:
N = 4
value[] = {1,8,3,4}
x = 0
Output: False
Explanation: For N = 4 ,x = 0 means
then lastNode->next = NULL, then
the Linked list does not contains
any loop.
Your Task:
The task is to complete the function detectloop() which contains reference to the head as only argument.  This function should return true if linked list contains loop, else return false.

Expected Time Complexity: O(N)
Expected Auxiliary Space: O(1)

Constraints:
1 ≤ N ≤ 104
1 ≤ Data on Node ≤ 103
```

```python
class Solution:
    #Function to check if the linked list has a loop.
    def detectLoop(self, head):
        head_fast = head

        while head_fast and head_fast.next:
            head = head.next
            head_fast = head_fast.next.next
            if head == head_fast:
                return True
        return False
```

```python
class Solution:
    #Function to check if the linked list has a loop.
    def detectLoop(self, head):
        
        #using two pointers and moving one pointer(slow) by one node and 
        #another pointer(fast) by two nodes in each iteration.
        slow = head
        fast = head
    
        #using a loop to move the pointers which stops when any of the pointers
        #or the pointer next to fast becomes null.
        while slow and fast and fast.next:
            slow=slow.next
            fast=fast.next.next
            
            #if both the pointers fast and slow point to same node which 
            #shows the presence of loop so we return true.
            if slow == fast :
                return True
        
        #if we reach here it means both the pointers fast and slow never 
        #point to same node so we return false.
        return False
```

### Remove loop in Linked List

```text
Given a linked list of N nodes such that it may contain a loop.

A loop here means that the last node of the link list is connected to the node at position X(1-based index). If the link
 list does not have any loop, X=0.

Remove the loop from the linked list, if it is present, i.e. unlink the last node which is forming the loop.


Example 1:

Input:
N = 3
value[] = {1,3,4}
X = 2
Output: 1
Explanation: The link list looks like
1 -> 3 -> 4
     ^    |
     |____|    
A loop is present. If you remove it 
successfully, the answer will be 1. 

Example 2:

Input:
N = 4
value[] = {1,8,3,4}
X = 0
Output: 1
Explanation: The Linked list does not 
contains any loop. 

Example 3:

Input:
N = 4
value[] = {1,2,3,4}
X = 1
Output: 1
Explanation: The link list looks like 
1 -> 2 -> 3 -> 4
^              |
|______________|
A loop is present. 
If you remove it successfully, 
the answer will be 1. 

Your Task:
You don't need to read input or print anything. Your task is to complete the function removeLoop() which takes the head 
of the linked list as the input parameter. Simply remove the loop in the list (if present) without disconnecting any 
nodes from the list.
Note: The generated output will be 1 if your submitted code is correct.


Expected time complexity: O(N)
Expected auxiliary space: O(1)


Constraints:
1 ≤ N ≤ 10^4
```

```python
class Solution:
    #Function to remove a loop in the linked list.
    def removeLoop(self, head):

        fast = head.next
        slow = head
        size = 1

        while fast != slow:
            if not fast or not fast.next:
                return head
            slow = slow.next
            fast = fast.next.next

        fast = fast.next

        while fast != slow:
            fast = fast.next
            size += 1

        fast = head
        slow = head

        for _ in range(size - 1):
            fast = fast.next

        while fast.next != slow:
            fast = fast.next
            slow = slow.next

        fast.next = None

        return head
```

```python
class Solution:
    #Function to remove a loop in the linked list.
    def removeLoop(self, head):
        
        #using two pointers and moving one pointer(slow) by one node and 
        #another pointer(fast) by two nodes in each iteration.
        fast = head.next
        slow = head
        
        while fast!=slow:
            
            #if the node pointed by first pointer(fast) or the node 
            #next to it is null, then loop is not present so we return 0.
            if fast is None or fast.next is None:
                return
            
            fast = fast.next.next
            slow = slow.next
            
        #both pointers now point to the same node in the loop.
        
        size = 1
        fast = fast.next
    
        #we start iterating the loop with first pointer and continue till 
        #both pointers point to same node again.
        while fast!=slow:
            fast = fast.next
            #incrementing the counter which stores length of loop.
            size+=1
        
        #updating the pointers again to starting node.
        slow=head
        fast=head
        
        #moving pointer (fast) by (size-1) nodes.
        for _ in range(size-1):
            fast=fast.next
        
        #now we keep iterating with both pointers till fast reaches a node such
        #that the next node is pointed by slow. At this situation slow is at
        #the node where loop starts and first at last node so we simply 
        #update the link part of first.
        while fast.next != slow:
            fast=fast.next
            slow=slow.next
        
        #storing null in link part of the last node.
        fast.next=None
```

### n’th node from end of Linked list

```text
Given a linked list consisting of L nodes and given a number N. The task is to find the Nth node from the end of the linked list.

Example 1:

Input:
N = 2
LinkedList: 1->2->3->4->5->6->7->8->9
Output: 8
Explanation: In the first example, there
are 9 nodes in linked list and we need
to find 2nd node from end. 2nd node
from end is 8.  
Example 2:

Input:
N = 5
LinkedList: 10->5->100->5
Output: -1
Explanation: In the second example, there
are 4 nodes in the linked list and we
need to find 5th from the end. Since 'n'
is more than the number of nodes in the
linked list, the output is -1.
Your Task:
The task is to complete the function getNthFromLast() which takes two arguments: reference to head and N and you need to return Nth from the end or -1 in case node doesn't exist.

Note:
Try to solve in a single traversal.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(1).

Constraints:
1 <= L <= 106
1 <= N <= 106
```

```python
def getNthFromLast(head,n):
    result_head = head
    step = 0
    
    while head:
        head = head.next
        if step >= n:
            result_head = result_head.next
        step += 1
        
    if step < n:
        return -1

    return result_head.data
```

```python
#Function to find the data of nth node from the end of a linked list
def getNthFromLast(head,n):
        
    #using two pointers, similar to finding middle element.
    curr_node = head
    nth_node = head
    
    #traversing first n elements with first pointer.
    while n :
        if n and curr_node == None:
            return -1
        curr_node = curr_node.next
        n-=1
    
    #now traversing with both pointers and when first pointer gives null 
    #we have got the nth node from end in second pointer since the first 
    #pointer had already traversed n nodes and thus had difference of n 
    #nodes with second pointer.
    while curr_node :
        curr_node = curr_node.next
        nth_node = nth_node.next
    
    #returning the data of nth node from end.
    return nth_node.data
```

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