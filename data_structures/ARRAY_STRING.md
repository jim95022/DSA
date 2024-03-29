# Array

An array is a collection of items stored at contiguous memory locations. The idea is to store multiple items of the 
same type together. This makes it easier to calculate the position of each element by simply adding an offset to a 
base value, i.e., the memory location of the first element of the array (generally denoted by the name of the array).

![array](../src/array.png)

> We can directly access an array element by using its index value.

The representation of an array can be defined by its declaration. A declaration means allocating memory for an array of a 
given size.

```python
arr = [10, 20, 30] # This array will store integer
arr2 = ['c', 'd', 'e'] # This array will store characters
arr3 = [28.5, 36.5, 40.2] # This array will store floating elements
```

> The idea of an array is to represent many instances in one variable

![array](../src/array1.png)

Types of arrays: 
1. One-dimensional array (1-D arrays): You can imagine a 1d array as a row, where elements are stored one after another.
2. Two-dimensional array: 2-D Multidimensional arrays can be considered as an array of arrays or as a matrix consisting of rows and columns.
3. Three-dimensional array: A 3-D Multidimensional array contains three dimensions, so it can be considered an array of two-dimensional arrays.

Types of Array operations:
- Traversal: Traverse through the elements of an array.
- Insertion: Inserting a new element in an array.
- Deletion: Deleting element from the array.
- Searching:  Search for an element in the array.
- Sorting: Maintaining the order of elements in the array.

Advantages of using Arrays:
- Arrays allow random access to elements. This makes accessing elements by position faster.
- Arrays have better cache locality which makes a pretty big difference in performance.
- Arrays represent multiple data items of the same type using a single name.
- Arrays store multiple data of similar types with the same name.
- Array data structures are used to implement the other data structures like linked lists, stacks, queues, trees, graphs, etc.

Disadvantages of Array:
- As arrays have a fixed size, once the memory is allocated to them, it cannot be increased or decreased, making it impossible to store extra data if required. An array of fixed size is referred to as a static array. 
- Allocating less memory than required to an array leads to loss of data.
- An array is homogeneous in nature so, a single array cannot store values of different data types. 
- Arrays store data in contiguous memory locations, which makes deletion and insertion very difficult to implement. This problem is overcome by implementing linked lists, which allow elements to be accessed sequentially.  

Application of Array:
- They are used in the implementation of other data structures such as array lists, heaps, hash tables, vectors, and matrices.
- Database records are usually implemented as arrays.
- It is used in lookup tables by computer.
- It is used for different sorting algorithms such as bubble sort insertion sort, merge sort, and quick sort.

## Array in Python

### Available methods
- append()
- insert()
- pop()
- remove()
- index()
- reverse()

```python
# importing "array" for array operations
import array
  
# initializing array with array values and signed integers
arr = array.array('i', [1, 2, 3]) 
 
# printing original array
print ("The new created array is : ",end=" ")
for i in range (0, 3):
    print(arr[i], end=" ")
print("\r")
 
# using append() to insert new value at end
arr.append(4)
 
# printing appended array
print("The appended array is : ", end="")
for i in range (len(arr)):
    print(arr[i], end=" ")
```

## Standard Easy Problems on Array:

### Find the largest three elements in an array

```
Given an array of N positive integers, print k largest elements from the array. 

Example 1:

Input:
N = 5, k = 2
arr[] = {12,5,787,1,23}
Output: 787 23
Explanation: First largest element in
the array is 787 and the second largest
is 23.
Example 2:

Input:
N = 7, k = 3
arr[] = {1,23,12,9,30,2,50}
Output: 50 30 23
Explanation: Three Largest element in
the array are 50, 30 and 23.
Your Task:
Complete the function kLargest() that takes the array, N and K as input parameters and returns a list of k largest element in descending order. 

Expected Time Complexity: O(N log K)
Expected Auxiliary Space: O(K)

Constraints:
1 ≤ N ≤ 104
K ≤ N
1 ≤ array[i] ≤ 105
```

```python
class Solution:
    # Function to return k=3 largest elements from an array.
    def kLargest(self, li, n, k=3):

        first_element, second_element, third_element = None, None, None

        for el in li:
            if not first_element or el > first_element:
                third_element = second_element
                second_element = first_element
                first_element = el
            elif not second_element or el > second_element:
                third_element = second_element
                second_element = el
            elif not third_element or el > third_element:
                third_element = el

        return first_element, second_element, third_element
```

```python
#Back-end complete function Template for Python 3

import heapq
class Solution:
    #Function to return k largest elements from an array.
    def kLargest(self,li,n,k):
        heap = []
        for value in li:
            #pushing the current value in Heap.
            heapq.heappush(heap, value)
            #if size of Heap becomes greater than k, we pop the element.
            if len(heap) > k:
                heapq.heappop(heap)
        
        ans = []
        
        #while heap is not empty, we store the top element in list and pop it.
        while len(heap) > 0:
            ans.append(heapq.heappop(heap))
            
        #reversing the list and returning it.
        ans.reverse()
        return ans
```

### Find Second largest element in an array

```text
Given an array Arr of size N, print second largest distinct element from an array.

Example 1:

Input: 
N = 6
Arr[] = {12, 35, 1, 10, 34, 1}
Output: 34
Explanation: The largest element of the 
array is 35 and the second largest element
is 34.
Example 2:

Input: 
N = 3
Arr[] = {10, 5, 10}
Output: 5
Explanation: The largest element of 
the array is 10 and the second 
largest element is 5.
Your Task:
You don't need to read input or print anything. Your task is to complete the function print2largest() which takes the array of integers arr and n as parameters and returns an integer denoting the answer. If 2nd largest element doesn't exist then return -1.

Expected Time Complexity: O(N)
Expected Auxiliary Space: O(1)

Constraints:
2 ≤ N ≤ 105
1 ≤ Arri ≤ 105
```

Time Complexity: O(n), where n is the size of input array.
Auxiliary space: O(1), as no extra space is required.

```python
class Solution:
    def print2largest(self,arr, n):
		
        first_element, second_element = None, None

        for el in arr:
            if first_element is None or el > first_element:
                second_element = first_element
                first_element = el
            elif (second_element is None or el > second_element) and el != first_element:
                second_element = el
        if second_element:
            return second_element
        return -1
```

Time Complexity: O(n), where n is the size of input array.
Auxiliary space: O(1), as no extra space is required.

```python
class Solution:

	def print2largest(self,arr, n):
		
        first_max, second_max = None, None

        for el in arr:
            if first_max is None or el > first_max:
                first_max = el

        for el in arr:
            if (second_max is None or el > second_max) and el != first_max:
                second_max = el

        if second_max:
            return second_max
        return -1
```

### Move all zeroes to end of array

```text
Given an array arr[] of n positive integers. Push all the zeros of the given array to the right end of the array while maintaining the order of non-zero elements. Do the mentioned change in the array in-place.

Example 1:

Input:
N = 5
Arr[] = {3, 5, 0, 0, 4}
Output: 3 5 4 0 0
Explanation: The non-zero elements
preserve their order while the 0
elements are moved to the right.
Example 2:

Input:
N = 4
Arr[] = {0, 0, 0, 4}
Output: 4 0 0 0
Explanation: 4 is the only non-zero
element and it gets moved to the left.
Your Task:
You don't need to read input or print anything. Complete the function pushZerosToEnd() which takes the array arr[] and its size n as input parameters and modifies arr[] in-place such that all the zeroes are moved to the right.  

Expected Time Complexity: O(n)
Expected Auxiliary Space: O(1)

Constraints:
1 ≤ N ≤ 105
0 ≤ arri ≤ 105
```

```python
class Solution:
	def pushZerosToEnd(self,arr, n):
	    
	    count = 0
	    
	    for index in range(n):
	        if arr[index] != 0:
	            arr[count] = arr[index]
	            count += 1
	   
	    while count < n:
	        arr[count] = 0
	        count += 1
    	    
```

```python
class Solution:
    def pushZerosToEnd(self,arr, n):
        count = 0
        
        # Traverse the array. If element encountered is non-
        # zero, then replace the element at index 'count'
        # with this element
        for i in range(n):
            if (arr[i] != 0):
                arr[count] = arr[i]
                count += 1
        
        # Now all non-zero elements have been shifted to
        # front and 'count' is set as index of first 0.
        # Make all elements 0 from count to end.
        while (count < n):
            arr[count] = 0
            count += 1
```

### Rearrange array such that even positioned are greater than odd

### Rearrange an array in maximum minimum form using Two Pointer Technique

```text
Given a sorted array of positive integers. Your task is to rearrange the array elements alternatively i.e first element should be max value, second should be min value, third should be second max, fourth should be second min and so on.
Note: Modify the original array itself. Do it without using any extra space. You do not have to return anything.

Example 1:

Input:
n = 6
arr[] = {1,2,3,4,5,6}
Output: 6 1 5 2 4 3
Explanation: Max element = 6, min = 1, 
second max = 5, second min = 2, and 
so on... Modified array is : 6 1 5 2 4 3.
Example 2:

Input:
n = 11
arr[]={10,20,30,40,50,60,70,80,90,100,110}
Output:110 10 100 20 90 30 80 40 70 50 60
Explanation: Max element = 110, min = 10, 
second max = 100, second min = 20, and 
so on... Modified array is : 
110 10 100 20 90 30 80 40 70 50 60.
Your Task:
The task is to complete the function rearrange() which rearranges elements as explained above. Printing of the modified array will be handled by driver code.

Expected Time Complexity: O(N).
Expected Auxiliary Space: O(1).

Constraints:
1 <= n <= 10^6
1 <= arr[i] <= 10^7
```

```python
#User function Template for python3
class Solution:
    ##Complete this function
    #Function to rearrange  the array elements alternately.
    def rearrange(self,arr, n): 
        
        left_index = 0
        right_index = n-1
        answer = []
        is_left = False
        
        for index in range(n):
            
            if not is_left:
                answer.append(arr[right_index])
                right_index -= 1
            else:
                answer.append(arr[left_index])
                left_index += 1
                
            is_left = not is_left
            
        for index in range(n):
            arr[index] = answer[index]

```

```python
#Back-end complete function Template for Python 3
class Solution:
    
    #Function to rearrange  the array elements alternately.
    def rearrange(self,arr, n): 
      
        #Initialising index of first minimum and first maximum element. 
        max_idx = n - 1
        min_idx = 0
      
        #Storing maximum element of array.
        max_elem = arr[n-1] + 1
      
        for i in range(0, n) : 
            #At even index, we have to put maximum elements in decreasing order. 
            if i % 2 == 0 : 
                arr[i] += (arr[max_idx] % max_elem ) * max_elem
                #Updating maximum index.
                max_idx -= 1
      
            #At odd index, we have to put minimum elements in increasing order.
            else : 
                arr[i] += (arr[min_idx] % max_elem ) * max_elem 
                #Updating minimum index.
                min_idx += 1
      
        #Dividing array elements by maximum element to get the result.
        for i in range(0, n) : 
            arr[i] = arr[i] // max_elem  
```
### Two Sum
```text
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
 

Constraints:

2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.
 

Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?
```

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        
        nums_dict = {}
        
        for num_index in range(len(nums)):
            delta = target - nums[num_index]
            if delta in nums_dict:
                return nums_dict[delta], num_index
            nums_dict[nums[num_index]] = num_index
```

### Segregate even and odd numbers
### Reversal algorithm for array rotation
### Print left rotation of array in O(n) time and O(1) space
### Sort an array in wave form
### Sort an array which contain 1 to n values
### Count the number of possible triangles
### Print All Distinct Elements of a given integer array
### Find the element that appears once in Array where every other element appears twice
### Leaders in an array
### Find sub-array with given sum

## String

> Strings are defined as an array of characters. The difference between a character array and a string is the string is 
> terminated with a special character ‘\0’.