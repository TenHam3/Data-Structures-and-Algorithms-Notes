# Data Structures and Algorithms Notes

## Arrays
### RAM

- RAM (Random Access Memory) is used to store variables and data structures
- Data structures are a way of organizing a collection of data
- RAM in any typical device is measured in gigabytes, which is approximately 10^9 bytes
  - A byte is 8 bits
    - A bit is a digit that can be represented by either a 0 or 1 and is the building block for the language used and understood by computers, called binary

- When visually represented, an array of elements will be lined up next to each other since an array is a contiguous block of memory that holds elements
- Each element will be shown with the value of the element and its address in the RAM (sometimes denoted with a $)
  - Since some data types take more bytes to be represented than others, addresses can increment by varying amounts

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/9fd7cf17-d033-4b97-97f9-d7e07ba2518d)
- The elements stored are integers, which take 4 bytes to store in memory so the addresses increment by 4

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/4a372212-e47e-40f9-95f8-07541cee2e31)
- The elements stored here are characters, which only take 1 byte to store in memory so the addresses increment by 1

### Static Arrays

Static Arrays are fixed size arrays that cannot resize when adding or removing values, resulting in the drawback of not being able to add or remove as many values as you want

- Since arrays are contiguous blocks of memory, adding an element when the array has reached maximum capacity does not work with static arrays because there is no guarantee that the next block of memory is available to allocate another element
  - Because of the index system of arrays, adding another element somewhere else in the RAM not adjacent to the array will most likely result in the wrong data being accessed as the operating system will try and access the element you added by going to the index after the last element in the array, which may contain some other data
- Reading/Writing to the ith element takes O(1) time because the indexing system allows the operating system to instantly access the ith element
- Insertion/Removal from the end of the array takes O(1) time because the indexing system allows you to instantly write to the last element via its index (removing would mean replacing it with a placeholder value such as 0)
- Insertion/Removal from the middle takes O(n) time because you may have to shift every element in the array before/after inserting/removing an element (this would happen if you were to insert/remove from the beginning of the array)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0c2c1850-c3f9-4758-9f04-1e4afbb71730)

### Dynamic Arrays

Dynamic Arrays are dynamically sized arrays that resize themselves if you add an element when at full capacity or remove an element at low capacity
- It does this by reconstructing a new array that is typically double the size of the original array and copying all the original elements from that array into the new one and freeing the memory that the old array was taking up. It then adds/removes the element the user wanted to before resizing
- The doubling in size makes pushing/popping an element take O(n) time on average because you wouldn't have to keep reconstructing the array after every push/pop
  - The amount of operations it takes to reconstruct an array by doubling is always dominated by the most recent reconstruction, meaning that the amount of operations it takes to reconstruct an array is always greater than or equal to the sum of the amount of operations it took from previous reconstructions. This also means the total sum of all operations it took to reconstruct the array into the latest size is less than or equal to twice the amount of operations the latest reconstruction took
    - Pushing an arbitrary n number of elements takes O(2n) time, which reduces to O(n) time because you can disregard constants when talking about O time complexity when the constants are adding or multiplying with variables

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0b0f20ca-e49a-4c6a-bb41-450a48a43760)

- Time complexity for each operation is the same for dynamic arrays as they are for static arrays

### Stacks

Stacks are LIFO (Last In First Out) data structures that support three operations: push, pop, and peek.
- Push adds an element to the "top" of the stack, or the end of the data structure you implement it with
- Pop removes an element from the top of the stack
- Peek accesses/reads the element at the top of the stack but doesn't remove it
- All these operations take O(1) time, which means stacks can be implemented using dynamic arrays since dynamic arrays support all these operations with the same time complexity

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/836ae469-39aa-442e-8356-8f275097fc3a)

- Stacks require a pointer or some way to keep track of the number of elements in the stack so you can maintain where the "top" of the stack is and know where to push/pop/peek the next element
- Stack operations only work on the topmost element so you cannot add, remove, or access elements from the middle of the stack
- A common analogy is imagining a stack of plates, where it is easy to add or remove plates from the top, but trying to add or remove plates from the middle or bottom is harder so you only do such operations on the top

## Linked Lists
### Singly Linked Lists

Linked lists are a series of nodes connected by pointers

- Nodes are objects that encapsulate data and pointers
- Singly linked lists are linked lists where the nodes only have a next pointer that points to the next node in the linked list
- Since linked lists are connected by pointers, the node objects don't have to be stored contiguously or in order in memory like data in arrays
- The first node in a linked list is typically referred to as the "head" and the ending node is referred to as the "tail"
#### Traversing a Linked List

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/b65ebf95-1971-4e98-9ebb-da17f49cd85b)

- You use a pointer to keep track of the current node you're on and move it to the next node in the linked list in a while loop
- Since the ending node points to null, the loop conditional will check for if the current node is a valid node or null, which would signify that we have traversed the entire linked list
- This is an O(n) time operation because you have to read n elements
#### Implementation
- You only need to create a node object or custom data type to make a linked list because the structure is automatically made from the properties of the node since they have the next pointer built in to them to connect them
- It is also helpful to keep track of the head and tail of the linked list by setting pointers to the first and last nodes, updating them if a new head or tail node is inserted into the linked list
#### Insertion and Removal
- Here we want to add a new node to the linked list with "purple" as its value

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/92596094-8759-431e-81c7-dbe1fd485347)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/89c3e845-c9d9-496c-aa59-0d4efc9375ac)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/09489cf4-e78c-4931-8946-8011fc9f8dcb)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c167cfde-5a64-4604-b3c2-96bc5903a612)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/3da1bdcb-7d43-4d75-ab43-3a346c3348e1)

- The first line of code uses the "tail" variable/reference to set the next pointer of node 3 to the newly added node
- The second line makes the tail variable reference the newly added node to signify that it is the new tail of the linked list
  - This can also be done by using tail = tail->next;
  - Because the tail variable still references the 3rd node, setting tail to tail->next makes the tail variable follow the 3rd node's new next pointer that points to the 4th node, making the tail pointer now reference the 4th node
- Adding a new tail node is an O(1) time operation because having the tail pointer means we don't have to traverse the entire linked list to access the current last node and change its next pointer to point at the node you want to add in and instead just execute the two lines of code no matter how many elements there are
- Removing a node from the beginning or end of the linked list takes O(1) time because you can just change the pointers to where the second node is the new head, the head points to the third node (if there is one), or the second to last node points to null (after freeing the last node if the compiler doesn't have a garbage collector)
- Insertion or removal in the middle takes O(n) time because you have to traverse the entire linked list to find the node that will point to the new node and then insert it or remove the node you wanted to remove

### Doubly Linked Lists

 Doubly linked lists are linked lists with each node having two pointers: one that points to the previous node in the linked list and one that points to the next node in the linked list. The head node's previous pointer points to null and the tail node's next pointer points to null.

 #### Insertion and Removal
 - Insertion is similar to how you would insert a node at the end of a singly linked list except you now have to update the new node's previous pointer to point at the previous tail node
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0abf4c2e-29b1-4a1a-9a37-f9e761158bb3)
  - The first line of code makes the previous tail's next pointer point to the newly added node. Then the new node's previous pointer is set to point at the previous tail node. Finally, the tail pointer gets set to point at the newly added node.
- Removing the tail node of a doubly linked list is also similar except the previous pointers make it easier since you can just follow the tail node's previous pointer to get to the new tail of the linked list
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/e0328c83-62db-4d5f-89ff-3a2cd0a3eef1)
  - The first line assigns a new pointer to point at the second to last node in the linked list by following the previous pointer of the current tail node. This makes it so we can use this node's pointers and reference in subsequent steps when we have to update this node's next pointer and the tail pointer. The second line makes the next pointer of the second to last node point to null to signify that it is the new tail of the linked list. Finally, the last line sets the tail pointer to point to the same node, and the previous tail node would be garbage collected if the compiler has a garbage collector. Otherwise, you would have to free the memory of the tail node first before executing the second line.
- Since these operations are the same no matter how many elements are in the linked list, these operations take O(1) time.
    - This means that stacks can be implemented using linked lists as well as arrays. However, it is less common to use linked lists because you lose the extra benefit of accessing any element in the stack at random that array offer with their indexing system. In linked lists, to access any random element, it would take O(n) time because you would have to traverse through the linked list node by node, but with arrays it is a O(1) time operation so that extra functionality is absent from linked list implementations.

#### Comparing Arrays and Linked Lists
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/e2f533f2-1886-4d9b-8807-334a6b351ee0)
- The advantage of arrays is that you can randomly access any element efficiently in O(1) time whereas in linked lists you would have to traverse the linked list starting from the head node every time until you found the i-th node
- Both arrays and linked lists can insert and remove elements from the end or beginning in O(1) time. However, linked lists have an advantage over arrays in this regard even though they both operate in O(1) time because trying to insert an element at the end of an array when it's at full capacity is not allowed if it's static and would be an O(n) time operation if it was dynamic since you would have to create a new array to resize and copy over each value of the old array. Arrays also have to shift every element over when removing from the beginning, meaning that this is also a O(n) time operation. Linked lists can always insert/remove from the beginning/end in O(1) time no matter how many elements there are because they do not have the restriction of being contiguous in memory and instead are connected through pointers. 
- The advantage of linked lists is that you can insert or remove elements from the middle in O(1) time because you can just change the pointers to point to the newly added node if you were inserting or the node that the removed node was pointing at if you were removing. However, in most cases, you would have to traverse the linked list in order to access the node you needed in order to insert or remove a node, which means it would take O(n) time.
- Overall, arrays have a slight advantage over linked lists since the random access with the indexing system is very useful and makes them more versatile than linked lists. Linked lists also practically don't have an advantage over arrays when it comes to insertion/removal from the middle since most of the time you would have to traverse the linked list in O(n) time to insert/remove a node. Even though the insertion/removal themselves are O(1) time operations, you would have to traverse the linked list to get to the insertion/removal point. Since traversal is a O(n) time operation, it dominates the O(1) time complexity of the insertion/removal, making the insertion/removal operation as a whole a O(n) time operation. 

### Queues

Queues are FIFO (First In, First Out) data structures that support two main operations: enqueue and dequeue
- Enqueue is similar to push for stacks, where you add an element to the end of the queue
- Dequeue is similar to pop for stacks except that you would remove an element from the beginning of the queue to preserve the FIFO structure
- This means that elements are removed in the same order they were added, hence why it is called a FIFO data structure. The first element that was added is going to be the first element to be removed.
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/01595808-4661-4a4d-af40-8322dd54b2d3)
- Just like stacks, these operations are meant to be done in O(1) time
    - Because of the FIFO structure of queues, dequeuing is not typically possible with arrays because when you remove an element from the beginning of the array, you would have to shift all elements down, making dequeuing a O(n) time operation.
- Linked lists are usually used to implement queues because they can insert at the end and remove from the beginning in O(1) time
- Implementation of a queue involves maintaining a current pointer that signifies the head of the linked list/beginning of the queue and a tail pointer to signify the end of the linked list/end of the queue.
- Enqueuing is just like adding a new node to the end of a linked list, where you make the current tail point to the new node and set the tail pointer to point to that node
- Dequeuing is similar to removing from the beginning of a linked list, where you just set the current pointer to point to current.next to effectively make the new head of the linked list the second node and removing the first node

## Recursion
### Factorial

Recursion is when a function calls itself with a smaller output

The factorial operation is just the multiplication of any integer with all subsequent integers counting down to 1
- This can be written as the formula n! = n * (n - 1)!, which lends itself to a recursive algorithm since it can be broken down into a smaller subproblem with the same algorithm

Recursive functions have two parts:
- The base case
- The function calling itself with a different input

There are two types of recursion: one-branch and two-branch. The recursion used to solve factorials involves one-branch recursion because each time you call the function, there is only one decision to be made in the decision tree (one calculation/function call for any level of the recursion).

#### Implementation and Explanation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/52ed6de4-8015-4bbb-84b7-4c87bc6a7d7e)

- The second return statement creates the subproblems of calculating the factorial of the smaller integers
  - This will keep executing until it gets down to 1, which is the base case handled in the first return statement
- After the base case has been reached, it will begin going back through the call stack to do every other recursive calculation since each call will have the previous factorial calculation solved

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/7de9f319-754b-44a4-9249-f9715d7a9b7d)

#### Time and Space Complexity
- Since you have to make a calculation for each level in the recursion, this algorithm takes O(n) time to execute. However, the recursive solution is actually worse than the iterative solution because it takes extra memory. This is because there will be n function calls, which take up space in the RAM for the parameters and function call itself, meaning that the space complexity is O(n) as well.

### Fibonnacci Sequence

The Fibonacci Sequence is a sequence of numbers created by taking the sum of the previous two Fibonacci numbers, with the zeroth Fibonacci number being 0 and the first Fibonacci number being 1. These will serve as the base cases for the recursion. The formula for computing the nth Fibonacci number is

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/73fce719-4620-4ea8-bffc-c37131ee88aa)

Calculating any Fibonacci number can be solved using two-branch recursion since the formula for calculating the nth Fibonacci number involves the same algorithm being used to break down the problem into basic conditions that serve as the base cases.

An example of the 5th Fibonacci number can be visualized using a tree. Each node in the tree has at most 2 branches, which is why this is called two-branch recursion. Each node that has two branches is a result of the fact that the formula to compute the nth Fibonacci number uses the same algorithm twice in its calculation.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/3acdc158-5be5-4639-9c3f-5400b2d34e58)

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/6aa48dec-5969-49f2-b460-138fbdfb8676)

- The first return statement takes care of the base cases where you would get to the zeroth or first Fibonacci number
- The second return statement applies the formula to compute the nth Fibonacci number using the same function, resulting in a recursive solution

#### Time Complexity

Because the formula requires two function calls, it ends up breaking each problem/node into two subproblems/nodes until the base case has been reached. This doubling nature means that the time complexity depends on the last level and however many nodes are in it.
- This is similar to how the time complexity for resizing a dynamic array was dominated by the last term in the reconstruction. The number of operations it took to do the latest reconstruction was greater than or equal to the sum of the total operations it took for all previous reconstructions. The maximum number of nodes in the last level is equivalent to 2^(n-1) since the longest path down the tree would count down to 1 from the number you started with to compute the nth Fibonacci term. It is n - 1 because the first level is indexed at 0, so for the maximum number of nodes at the last level of the decision tree for the 5th Fibonacci number, there would be a maximum of 2^4 = 16 nodes.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/585a171a-14e5-4aa0-b796-faf765c1769c)

- This gives an upper bound for how many nodes can be in the last level, which also means that it can serve as the time complexity since each node represents a calculation being made and the number of calculations is dominated by the number of nodes in the last layer. Since the total number of calculations that it took to compute the nth Fibonacci number is less than or equal to 2 * 2^(n - 1), the time complexity simplifies to O(2^n).
