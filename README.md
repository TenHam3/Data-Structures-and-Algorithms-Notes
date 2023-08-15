# Data Structures and Algorithms Notes

## Arrays
### RAM

- RAM (Random Access Memory) is used to store variables and data structures
- Data structures are a way of organizing a collection of data
- RAM in any typical device is measured in gigabytes, which is approximately 10<sup>9</sup> bytes
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

![image](https:github.comTenHam3Data-Structures-and-Algorithms-Notesassets1097058113da1bdcb-7d43-4d75-ab43-3a346c3348e1)

- The first line of code uses the "tail" variablereference to set the next pointer of node 3 to the newly added node
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
![image](https:/github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0abf4c2e-29b1-4a1a-9a37-f9e761158bb3)
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
- This is similar to how the time complexity for resizing a dynamic array was dominated by the last term in the reconstruction. The number of operations it took to do the latest reconstruction was greater than or equal to the sum of the total operations it took for all previous reconstructions. The maximum number of nodes in the last level is equivalent to 2<sup>(n-1)</sup> since the longest path down the tree would count down to 1 from the number you started with to compute the nth Fibonacci term. It is n - 1 because the first level is indexed at 0, so for the maximum number of nodes at the last level of the decision tree for the 5th Fibonacci number, there would be a maximum of 2<sup>4</sup> = 16 nodes.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/585a171a-14e5-4aa0-b796-faf765c1769c)

- This gives an upper bound for how many nodes can be in the last level, which also means that it can serve as the time complexity since each node represents a calculation being made and the number of calculations is dominated by the number of nodes in the last layer. Since the total number of calculations that it took to compute the nth Fibonacci number is less than or equal to 2 * 2<sup>(n - 1)</sup>, the time complexity simplifies to O(2<sup>n</sup>).

## Sorting 
### Insertion Sort

Insertion sort is an algorithm that involves breaking the array or any data structure down to smaller subproblems such as a subarray and sorting them, gradually working your way back to the original size each time. The process of breaking down the array into smaller subarrays stops when it gets to the zeroth index, making it a subarray of size 1 because that will always be in sorted order since there are no elements to compare the single element to. This is when the algorithm begins working its way back to the original size, now sorting a subarray of size 2 with the zeroth and first elements and so on. In each iteration the algorithm encounters an element that is greater than the previous element, it stays at the position it was at and moves on to the next iteration/subarray because the previous iterations that sort the smaller subarrays means that every element before was also smaller, or in the order it should be, so there would be no need to go back and compare it to every element before. However, if the algorithm comes across an element smaller than the previous one, it will have to swap positions and compare it to its new previous element. This process will continue until the element is greater than its previous neighbor or it lands in the first position/zeroth index, maintaining the sorted order.

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/8a1b60e0-7001-4ff6-b58f-7c5896c3d79c)

- Although this algorithm involves breaking the array down into subproblems, the iterative solution is simpler and more efficient in both time and space complexity
- The algorithm starts with a for loop that loops through the entire array starting at index 1 since the first element at the zeroth index is already sorted so there's no need to start there
- We then create a pointer j to keep track of the element we're comparing the current element to. The j pointer starts one index behind the current last index in the subarray of the current iteration.
- The while loop conditions check for if the jth index is greater than or equal to 0 to safeguard from the index going out of bounds and if the element in front of the jth index is less than the element at the jth index. This essentially is checking for if the new element of the subarray is less than the previous element.
  - If these conditions are satisfied, the while loop is entered and the swapping process begins. You first save the newly added element in a temporary variable, replace it with the previous element, and put it in the previous position. Then you decrement j to check if it is smaller than its new previous neighbor.
- At the end, the function returns the sorted array

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/092cbe63-385a-438b-91a1-d31378fc9c3e)

#### Stability 

Stable sorting is when a sorting algorithm preserves the relative order of elements in a data structure, so if there are duplicate elements, they are arranged in the order of which came first/from lowest index to highest index. Unstable sorting algorithms may or may not preserve the relative order. There is no guarantee that an unstable sorting algorithm will maintain the relative order of elements.

- Insertion sort is a stable sorting algorithm because the condition for performing the swap of elements checks for if the jth element is greater than the j + 1th element, not greater than or equal to. This means that any duplicate elements being compared will not enter the while loop and trigger a swap, maintaining the relative order.

#### Time Complexity 

In the best case scenario, that is, when using insertion sort on an already sorted array, it runs in O(n) time because it has to traverse the entire array to check if they are smaller than the previous element. Even though the implementation includes a nested loop, it runs in O(n) time in this case since the array is already in sorted order, meaning it doesn't meet the while loop condition that checks whether the j + 1th element is less than the jth element and thus never runs the while loop. In the worst case scenario where the elements are stored in reverse order, insertion sort runs in O(n<sup>2</sup>) time because you would have to iterate through the entire array from the for loop and perform n - 1 swaps every iteration where n is the size of the current subarray. This amounts to O(n<sup>2</sup>) time complexity. Even though it doesn't perform n<sup>2</sup> operations, the time complexity is denoted as O(n<sup>2</sup>) because the amount of operations is bounded by n<sup>2</sup> since that is the maximum number of operations possible for a nested loop (doing n operations/swaps for n iterations).

### Merge Sort

Merge sort is a sorting algorithm that involves recursively breaking down the array into halves, sort the halves, and merge the halves together. The algorithm first breaks down the array until the halves reach a size of 1 because arrays of size 1 are automatically sorted. It then merges the two halves together in sorted order by going through each array starting from the zeroth index of both, comparing the two elements, placing the lesser of the two elements into the array, going to the next element of the array and iterating this process until there are no more elements left from both halves to merge. When one subarray runs out of elements to add while the other still has more, the algorithm will just merge the remaining elements from that array into the merged array. It keeps merging these sorted halves until we are back to the original array's size and both sorted halves have been merged, leaving you with the original array in sorted order. The technique of repeatedly splitting the array into approximately equal halves is called divide and conquer because we are dividing the original problem into smaller and more manageable subproblems and solving them first before solving the original larger problem. 

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/a0153f86-0921-4088-b6e3-af2585910cc5)

- The function passes in the array that will be sorted along with the starting and ending indices because that will make it easier to recursively call the function on the smaller subarrays without having to actually create the subarrays in memory and instead just operate on the smaller index ranges
- The first line checks for the base case if the current subarray is of size 1. It does this by seeing if the difference between the ending and starting index plus one is less than or equal to 1 because if the subarray was of size 1, both the starting and ending index would be the same so their difference would be 0 and adding 1 to it means that the size is 1.
- The next line calculates the middle index of the current array to keep track of where to divide the array into its smaller subarrays
- The next two lines call the mergeSort function on the two halves of the array to achieve the recursive step of dividing the problem into smaller subproblems
- The next line merges the two halves together before returning the new sorted array back up the call stack to merge with other sorted halves or to return the original array in sorted order. The merge function is where the sorting occurs since that's how the algorithm works. It goes through both sorted halves one by one, comparing one element of one half to one element of the other and placing them in the array depending on which is smaller. This is the merge process.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/8a4a1832-527c-411b-a433-258ff04a346a)

- The first two lines copy the left and right halves of the array into temporary subarrays so that the algorithm can iterate through each half and compare their elements to merge them in sorted order. The second argument in the function that makes the copy array for both halves is the ending index of the subarrays and it is exclusive, meaning that the element at that index is not included which is why the left half ends at arr.begin() + m + 1 and the right half ends at arr.begin() + e + 1 instead of just arr.begin() + m and arr.begin() + e.
- The next 3 lines declare variables to serve as pointers. The first two are pointers for the left half and right half of the array and the last pointer is to keep track of the position to place the next element.
- The while loop is where the merging occurs. The conditions check for if either of the pointers is out of bounds/if either of the arrays has no elements left to add. Then the loop checks for if the current element in the left array is smaller than the current element in the right array. If so, it will add that element into the kth index of the array and simultaneously increment i to move the pointer to the next index of the left half (this is done by utilizing the increment operator i++ since it allows the program to use the current value of i before incrementing it). If the element in the right half is smaller, it will add that element to the kth index and increment j. Afterwards, the while loop increments k to move the pointer to the next position in the array and the while loop continues.
- After the while loop is done, there will only be one half that will have merged all of its elements so the remaining while loops check to see which half still has elements to add and adds them in. Since the halves should be sorted, they just add the elements in the order they are in the subarray.
    - The piece of code used for i pointer and j pointer is actually referred to as the two pointer technique and is extremely useful when we have two arrays and need to go through them simultaneously to perform some logic. This could actually be used to combine two arrays and do so in O(n) time.

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0accd1be-0ac1-4145-9486-353f8b15a2ac)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/d189a214-3c21-46a8-a0d6-50c820cc8e18)

#### Time and Space Complexity

The number of times you can split the array into halves is the same as the amount of levels there are in the decision tree. In order to figure this out, we construct an equation to figure out how many times we can split an array of n elements in half until we get to 1, the base case. The equation is as follows:
- $n/{2^x} = 1$

Rearranging gives us

- $n = 2^x$

To solve for x, the number of times you can divide the array by 2 to get to subarrays of size 1, you can take the log base 2 of both sides

- $\log{_2}{n} = \log{_2}{2^x}$

You can simplify the right side using logarithmic rules by moving the x out in front

- $\log{_2}{n} = x\log{_2}{2}$

Taking the log of a number that is the same as the base is 1 so

- $\log{_2}{n} = x$ or $x = \log{n}$ since in computer science log is usually assumed to be base 2

So the number of times you can split the array in half is $\log{n}$

However, this is not the full time complexity as it is only the number of levels we have for the decision tree. We need to calculate the total number of operations it takes to execute the algorithm by determining how many operations are being done per level. In the merge function, we are taking two sorted halves of the array and placing their elements into the array. For each level, you are merging n elements into the arrays and even in the bottom level where the base case is reached, you still have to visit the elements and determine their size to verify that it is the base case, meaning that it also takes n operations. This means that we are doing n operations for every level of the decision tree and we have $\log{n}$ levels to the tree so the total time complexity for merge sort is O($n\log{n}$).

The space complexity is O(n) because at any given level there will be n total elements allocated during the merging processes.

#### Stability

Merge sort is a stable sorting algorithm because during the merging process, you can make the comparison step left-biased so that the elements that appeared earlier in the array come before later duplicates. This is shown in the merge function code where it checks if the ith element in the left half is less than or equal to the jth element of the right half. So if there was a duplicate element, the one on the left side gets put in first since it satisfies the if statement condition to add the element from the left side, maintaining the relative order.

### Quick Sort

Quick sort is another recursive sorting algorithm that picks an index called a pivot and partitions the array such that all values to the left of the pivot are less than it and all values to the right of it are greater than it. For this implementation, the pivot will be the last index, so the algorithm iterates through all values in the array besides the last one, sorting them based on whether they are less than or greater than the pivot. The pivot can be at a different index depending on the initial size and order of the array. The partition is done by swapping elements that are less than the pivot to the beginning of the array, incrementing the index of the pointer for this position for every swap that occurs. After every element has been iterated through and we get to the pivot, we swap the pivot with the element at the index where the swap pointer is at, which partitions the array to where all elements left of the pivot are less than it and all elements to the right of it are greater. Once the array is partitioned, the recursive step begins and we run quick sort on the newly partitioned array and keep doing so until we get down to subarrays of size 1 just like merge sort.

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/30ee03bf-2254-4820-906b-013bfb341ede)

- The base case is the same as merge sort so it checks whether the current array is of size 1
- The next two lines initialize the pivot at the end of the array and the "left" pointer that functions as the pointer that indicates where to swap the next element that is less than the pivot
- The for loop iterates through the entire array (except for the last index because that's where the pivot is) and compares each element to the pivot. If it is less than the pivot, it performs a swap with the element at the left pointer and increments the left pointer.
- After every element has been iterated through, the next two lines swap the pivot with the element at the left pointer to create the partition. Now, all elements left of the pivot are less than or equal to the pivot and all elements right of the pivot are greater than or equal to the pivot.
- The next two lines implement the recursive step of quick sort, performing the function on the left and right halves of the array. Note that the left side's ending index is at left - 1 and the right side's starting index is at left + 1 because the partition makes it so that the pivot is already in the spot it should be since all elements before are less than or equal to it and all elements after are greater than or equal to it, so no matter what happens in the sublevels of the recursion, it will always be in the spot it needs to be for it to be sorted.

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/fefe0249-e38a-4d90-815f-d973038b8e13)

#### Time Complexity

The best case scenario for quick sort is when you can keep partitioning the array down the middle such that the array gets divided into two equal subproblems. Since we are doing n operations for each level of the decision tree and the nature of dividing the problem into two equal halves every time makes the height of the tree $\log{n}$, the best case time complexity would be O($n\log{n}$). This only occurs when the pivot is the median of the array. In the worst case, the pivot is the smallest or largest value of the array, making the partitions into two unequal subarrays: one where it is just the pivot and another that includes the rest of the array. If this happens at every level, we will be doing approximately n operations on n levels of the decision tree instead of just $\log{n}$ levels so the worst case time complexity would be O($n^2$). In the implementation above, this would happen when the input array is already sorted since the pivot would always be the greatest element. The worst case scenario does not happen often so on average, the time complexity of quick sort is O($n\log{n}$).

#### Stability

Quick sort is not a stable sorting algorithm because the algorithm swaps non-adjacent elements, which doesn't guarantee it preserves the relative order of elements. For example, an array such as [7, 3, 7, 4, 5] will work out like this:

- First swap: [3, 7, 7, 4, 5]
    - The 7 that was initially in the 0th index swapped with the 3 and is now in the 1st index
- Second swap: [3, 4, 7, 7, 5]
    - The 7 that was initially in the 0th index swapped with the 4 that was in the 3rd index and is now after the 7 that was initially in the 2nd index

### Bucket Sort

Bucket sort is a sorting algorithm that has a restriction of only being able to be used on an array of values within a finite range. If the range is too big, you cannot use bucket sort. Bucket sort works by creating buckets that map to the values in the array. Buckets are just indices of an array that will map to the values in the array that holds the values that need to be sorted. Each bucket will have a value associated with them that tells you how many of those elements there are in the array. After all the buckets are made and filled up, the array will then be overwritten with new values given by the buckets, iterating through each bucket and writing however many of that element are meant to be added to the original array. 

#### Implementation 

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/0140bd6b-238d-4f52-9a2e-89da4e673f6b)

- The first line creates the array that holds the buckets and initializes them all to 0
- The for loop counts the frequency of each of the elements in the array by iterating through the array and incrementing the corresponding bucket for each value
- The next few lines are where the original array gets overwritten with the new values in sorted order. First, it initializes a variable i to 0 to indicate the current index of the array to add the next element. The outer for loop iterates through all the buckets and the inner for loop iterates the number of times equal to the frequency of the number associated with that bucket. Inside the inner loop, it overwrites the element at index i with the number associated with that bucket and increments i.

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/28359c88-0bb6-4f41-be2e-6cc5fd44266b)

#### Time and Space Complexity

The first part of the algorithm fills the buckets by iterating through the entire array to count the frequency of each value in the array. The second part goes through each bucket and puts in the corresponding number of values into the array. When thinking about what the algorithm is doing, it just goes through all the buckets and puts the same number of elements in as there were originally so even though there is a nested loop, the algorithm only really performs n operations, one for each time a number from a bucket gets written to the array. The total number of iterations of the inner loop amounts to n. Adding the two parts together, the time complexity would be O(2n), which simplifies down to O(n). The space complexity comes out to be however big the range of values is for the array because you have to allocate a bucket for every value within the range. Since bucket sort is meant to be used on arrays with a finite range of values, the range is going to be constant, making the space complexity O(c) where c is the constant representing the range, which simplifies to O(1).

#### Stability

Bucket sort is not a stable sorting algorithm because it overwrites values instead of swapping them, effectively creating a new array of values with a different relative order. Bucket sort only cares about the frequency of each value and places them in, overwriting the original value stored so any relative order that was established is removed and makes it unstable.

### Comparison of Different Sorting Algorithms

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/08937f76-7470-4b88-a5ae-c9faac9c5826)

## Binary Search

### Search Array

Binary search is a search algorithm that cut down your search space in half each iteration until the desired element is found or every element in the array is searched and is still not found, meaning that the desired element is not in the array. The algorithm starts by picking the middle element in the array and comparing it to the target value. Binary search will either return the element's index if the middle element is the target or run on the left or right half of the array depending on whether the middle value is greater than or less than the target, respectively. Binary search can only be successfully executed on an array that is already in sorted order because otherwise there would be no guarantee that the target value will be in the half it's supposed to be based on the comparison step. 
- Ex: If binary search were to run on the array [1, 4, 3, 2, 5] and the target value was 4, it would compare 3 to 4. Since 3 is less than 4, it would disregard the left half of the array and run binary search on the right half, even though 4 was in the left half of the array.

#### Implementation 
Binary search can be implemented using recursion or iteration but iteration is simpler

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/763c91bb-7cf6-4054-b3ad-a34196d6d46d)

- The first line creates two pointers to keep track of the boundaries of the current subarray we are running binary search on
- The while loop is where we iteratively run binary search on increasingly smaller subarrays until the target is found or until no more elements are left to search. The condition checks if the left pointer is less than or equal to the right pointer because if this condition is satisfied, it means there is still at least one element to search in the search space. If the left pointer was greater than the right pointer, that would mean they crossed and there would be no more elements to search.
    - The first thing the while loop does is calculate the middle of the current subarray by taking the average of the left and right indices
        - This implementation of taking the average of the left and right indices has a bug if the sum of the left and right indices exceeds the maximum integer value ($2^{31} - 1$) so a better implementation would be to use something like this:

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/f931a3be-f160-4cc2-bb1b-8841b8a022b3)

- It then goes through a series of if-else statements to determine if the element is found or if binary search should be run on the left or right half
  - If the target is greater than the middle element, it will shift the left pointer to middle + 1 to create the new boundary for the subarray, effectively cutting the search space in half by disregarding the left half of the array
  - If the target is less than the middle element, it will shift the right pointer to middle - 1 for the same reason
  - If neither of these conditions is met, it will return the middle index because that must mean that the element has been found
- If the while loop exits, that means that the pointers have crossed and all elements have been effectively searched without returning an index, meaning that the element was not in the array so we return -1, an invalid index

#### Visualization 

- Target exists in the array

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/9a7cc808-23a5-48ef-bf73-ffb0d059b351)

- Target does not exist in the array

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c9c8a738-c158-41b9-b547-f86dc1206406)

#### Time and Space Complexity

Similar to merge sort, we are dividing the problem in half for each iteration that we execute binary search on the array. In the worst case scenario where the search space gets reduced all the way down to a size 1 subarray, it would take O($\log{n}$) time since that's how many times you can divide the array in half until you get to size 1. Since our implementation didn't allocate extra memory to create the subarrays and instead only created a few pointers, the space complexity would be O(1).

### Search Range

Sometimes you won't run binary search on an array but on a range of numbers. You also might not be given a target value and you just have to search the range of numbers until the algorithm either finds a specific number that satisfies some condition(s) or no number within the range was found that satisfies the condition(s). This means that when running binary search on a range of numbers, each iteration only determines whether the middle value satisfied the condition(s) or not and whether to search lower or higher. There is no target value to compare the middle element of each iteration to so this version of binary search must have some way to determine these things, usually a helper function. 
- Ex: A friend picks a number at random from 1-100 and wants you to figure it out. He only tells you whether your guess was correct, or if it was too high/low. He doesn't give you a target value since that would defeat the purpose of the game so you have to guess a number based on his feedback of your guesses.

#### Implementation

Helper function to determine if the number is too high, too low, or correct

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/7c63a045-bc67-45ef-84a4-6db543587c4c)

Binary search algorithm that uses the helper function to determine where to search next iteration

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/aa76a285-de10-40a2-990b-1ea736fd31f6)

- In general, the helper function may have other conditions  that may be more sophisticated that need to be satisfied and not just picking a certain number or value

#### Time Complexity

Just like the previous section of binary search, we are cutting the problem down in half each iteration so the time complexity of executing binary search on a range would be O($\log{n}$) where n is the range instead of array size

## Trees

### Binary Tree

Binary Trees are data structures that also involve nodes and pointers to connect different data values, except instead of being represented as directed lines like linked lists, binary trees are visually represented like an upside-down tree or family tree, where there is a sole node at the top to start the tree and branches down and out to other nodes. There are no previous and next pointers, but rather left and right pointers to create this branching-out structure instead of a straight line like a linked list. Binary trees are not allowed to have cycles, meaning that there is no path to be taken that will result in an infinite loop of visiting the same nodes (assuming the pointers are undirected, meaning that you could travel in either direction of the pointer), unlike linked lists where the tail could point back to the head.

- The sole node at the top where all subsequent nodes originate is called the root node. All nodes in the tree can be reached starting from the root node.
- Any node that points to other nodes is called a parent node and any nodes that are connected from a node higher in the tree are called child or children nodes. The root node does not have any parents.
- Nodes that share the same parent are called sibling nodes
- All nodes have to be connected through pointers. No node can be off the tree by not being pointed at by any of the other nodes in the tree.
- Binary trees restrict their nodes to where any node can have at most two child nodes
- Any node that is at the lowest level of its path of the tree will have no child nodes and are called leaf nodes
    - All binary trees are guaranteed to have leaf nodes because of the "no cycle" rule of binary trees that prevent nodes from pointing to their parent or sibling nodes. This ensures that the bottom nodes will not have any nodes to point to and thus become leaf nodes.
- Any node that is at a lower level of the tree relative to another node is said to be the descendant of that node if there is a path that connects them
- Any node that is at a higher level of the tree relative to another node is said to be the ancestor of that node if there is a path that connects them
- Another property of a node in a binary tree is called the height. The height is determined by how many nodes there are from any particular node to its lowest descendant. A leaf node with no children have a height of 1 because there is only 1 node in that path. A node with only 1 descendant has a height of 2 since the path from that node to its lowest descendant has 2 nodes.
    - Sometimes the height is calculated based on how many pointers there are to get to the lowest descendant of that node, making the lowest height start at 0 instead of 1. In this system, leaf nodes would have a height of 0 and a node with only 1 descendant has a height of 1. This depends on preference and is not that important.
- The opposite of height in a binary tree is depth. The depth is calculated by determining how many nodes are in the path that connects any particular node to the root node. The root node would have a depth of 1, the children of the root node would have a depth of 2, and so on.
    - Same as height, the depth is sometimes calculated based on the amount of pointers it takes to get to the root and starts at 0.

### Binary Search Tree

Binary Search Trees are a special type of binary trees that are sorted in a certain manner. For every node in the binary search tree, all its descendants on the left side are less than it and all descendants on the right are greater than it. This grouping of descendants is called a subtree. In general, a subtree is any number of nodes that form the same tree structure with the "root node" being a child node (if you pretended that it didn't have a parent). Binary search trees do not allow duplicates so this will not be an edge case that needs to be handled.

#### Benefit of Binary Search Trees

The benefit of a binary search tree is the same as having a sorted array. Searching for an element in a binary search tree is more efficient and will take O($\log{n}$) time on average, just like how arrays can run binary search in O($\log{n}$) time.

Because of the way binary search trees are structured, the algorithm for searching for an element in a binary search tree is similar to how binary search on an array functions, where it splits the problem in half every time. For binary search trees, instead of moving to different indices and tightening the boundaries, you can just follow whichever path is necessary to find the element based on the comparison of the target value and the current node's value. The property of binary search trees that order them makes this easy because you can take the left path if the target value is smaller than the current node's value, since all node values left of the current node are smaller, or the right path if the target value is greater than the current node's value since all node values right of the current node are larger.

#### Search Implementation

Searching a binary search tree can be done recursively or iteratively but the recursive solution is easier to learn and code, so that will be how we implement the search algorithm. Even though the nodes in binary search trees can have two children, the search algorithm is one-branch recursion because you only follow one path of the binary search tree and never go back up to the paths you skipped over.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/1dd622c9-5bdc-4c28-9d0d-bc9aa480469f)

- The first line is the base case of the recursion, which checks to see if the current node is null. If the current node is null, it means that we ran out of nodes to search and return false to signify that the element was not found in the binary search tree.
    - The !root checks if the current node is null because any value that isn't null is treated as the boolean value True and null is treated as False. This means the statement !root triggers False and does not execute the code inside the if-statement when the current node contains a value and triggers True when the current node is null.
- The following if-else statements are the comparison steps that tell us which direction to search in next. If the target is greater than the current node, it will recursively search the right side and if the target is less than the current node, it will recursively search the left side. If neither of these conditions are true, that means we have found the value and the last else-statement executes, returning true.

#### Time Complexity

Since this functions similarly to binary search on an array, the time complexity on average is O($\log{n}$). However, this only applies to binary search trees that are balanced, meaning that for the entire tree and every subtree, the height will be roughly the same and may differ by only 1. If you had a binary search tree where your root node was the smallest or largest value in the tree and each subsequent node was incrementing or decrementing, it would essentially become a linked list because there would only be one straight path to traverse. In the worst case, this is how our tree would be structured and the target would be the leaf node at the bottom level, meaning we would have to traverse the entire tree, visiting each node until we found the leaf node. This would take O(n) time. Both of these time complexities can be expressed as O(h) where h is the height of the tree. This applies to a balanced binary search tree because you would be dividing the problem by 2 for each iteration until you get to the target, making the height of the tree $\log{n}$. This also applies to the one-path binary search tree because the height would just be however many elements there are in the tree, which is n.

### BST Insert and Remove

The main advantage of using binary search trees over sorted arrays is that binary search trees can insert and remove elements in O($\log{n}$) time (assuming the tree is roughly balanced) whereas arrays do them in O(n) time. 

#### Insertion Implementation

Insertion in a binary search tree works by finding the insertion point of the node we want to add through traversing and comparing values of the new node with the current node. When it gets to a null position in the tree, it will create the node and make it the new child of the current node by returning it to the parent as its left or right pointer depending on the comparison of values between the two nodes. This means that insertion for a binary search tree inserts nodes as leaf nodes. 

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/1aaefff1-baea-4026-b30e-2caebb617d11)

- The first line is the base case of the recursion and is the same as searching. It checks for if the current node is null except that if it is it will return a newly created node with the value passed in. This is going to be the new node we want to insert into the tree once we do get to the bottom of the tree where the insertion point will be.
- The if-else statements compare the values of the current node with the node we want to insert. If the value of the new node is greater than the current node, it will traverse the right half of the subtree by recursively calling insert on the right child of the current node. The same goes for the left side of the current node if the value of the new node is less than the current node.
- The last return statement will return the node current node of that iteration of the recursion to the appropriate child of its parent. This basically just returns the same subtree to the root of the entire tree except with the newly inserted node as a new leaf once it works its way back up the tree and returns the root's child node to the root.

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/60d9d686-4fea-4aad-99cf-5be2c847fc40)

#### Removal Implementation

When removing a node, there are two cases we have to consider: the node we want to remove has 0 children or 1 child, and another case where it has 2 children. Similarly to insertion, we will still have to traverse through the tree and search for the target node but instead of creating a node at null we instead remove a node and adjust the tree to replace the removed node. In the first case where the target has 0 or 1 child, we would simply return one of the target value's children, whether it be null if it had 0 children or the only child it has in the 1 child case. In the 2 children case, we would replace the target node with the smallest node in its right subtree, called its in-order successor, because it would preserve both the balance of the tree and the ordered structure of the binary search tree. It would preserve the order because we know that since all values left of the target are going to be smaller than it and all values right of the target are going to be greater, the same will apply to the smallest value of the right subtree. All values left of the replacement node will still be less than it since it was greater than the removed node and all values right of it will still be greater since it was the smallest value in the right subtree.

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c6cb474a-5e7f-4d2b-8f70-8c56019c65a3)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/14f0e3c5-af9b-47cf-995f-1ac51e11be13)

The top function is a helper function that finds the minimum value in a given tree. This will be used to find the minimum value node of the right subtree of the target node if it has two children. The bottom function is the removal function.

- Minimum Value Node
    - In the first line, we create a variable curr to keep track of the current node that we're on when traversing through the tree
    - The while loop traverses through the tree until it finds the minimum value node of the tree. The condition checks if both the current node and its left child are valid nodes, meaning that they aren't null. If they are, it will change curr to be the left child of the current node, traversing the left path of the tree every time because that's where the smallest values will be. Once it reaches a node where the left child is null, it will exit the while loop and return the current node, which should be the minimum value node.
    - The traversal is done iteratively instead of recursively because we are just following the left path every iteration so it is essentially the same as traversing a linked list, which was also done iteratively.

- Removal
    - The first line checks if the current node is null and returns a newly created node with the value we want to remove if it is null
    - The following if-else statements are similar to the insertion algorithm where you compare the target node's value with the current node's value to see which path to traverse. If the target value is greater than the current value, it will recursively call remove on the right child of the current node and return the result on the right child. The same goes for the left side if the target value is less than the current value. Returning the result serves the same purpose as in the insertion, which reassigns the pointers leading up to the root to make the new tree with the target removed and the replacement moved to the target's original position. If neither of these conditions are met, that means we are at the target node and we can begin the removal process.
      - The first two if-else statements check if the left and right children exist. If the left child does not exist, it will return the right child. Then it checks if the right child exists and if it doesn't, it will return the left child. These two if-else statements handle case 1 where the target node has 0 or 1 child because if the left doesn't exist, the target will have at most 1 child if the right exists and the same goes for the second condition.
      - The last else statement handles case 2 where the target node has 2 children. First, it finds the minimum value node of the right subtree and saves it as a variable to use later. It then replaces the current node's value with the min value node and then runs the remove function on the right child of the new replacement node to remove the old minimum value node.

#### Visualization of Case 1

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/764ca444-a1bc-4cbc-b78c-7be6acebead6)

#### Visualization of Case 2

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/429d3560-6333-41c9-8cd6-bbc83fe3491e)

#### Time Complexity 

The time complexity for both insertion and removal depends on the height, just like searching. This makes sense because the main bulk of the algorithm is finding the insertion/removal point by traversing through the tree and since the time complexity of searching is O(h), this is also the time complexity of insertion and removal. If the tree is balanced, the height will be $\log{n}$ for a similar reason to merge sort. In merge sort, the height of the decision tree was $\log{n}$ because it was based on how many times the array could be split in half until we get to 1. In a similar vein, the height of a binary search tree is based on how many times you can divide the bottom level until you get to one node, which would be the root node. However, as stated earlier with search, the worst case scenario is when the tree is unbalanced and is either left or right-skewed, making these operations operate in O(n) time.

### Depth-First Search

Depth-first search (DFS) is a traversal algorithm for trees that works by traversing down the tree first before moving laterally, prioritizing depth over breadth. The goal is to reach as deep as possible in the tree for every path that leads to a leaf node before searching all nodes on the same level as the nodes visited further up. There are three ways of implementing depth-first search: inorder, preorder, and postorder. For binary search trees, the inorder traversal is when you visit the left subtrees of a node, the node itself, and the right subtrees in that order to visit every node in sorted order. This is because of the organization of nodes in a binary search tree where all descendants left of a node are less than it and all descendants right of it are greater than it so going down and left of the tree would give you the lowest value and working your way up and right will visit the nodes in order. The preorder traversal that prioritizes left before right is when you visit the node itself first, then the left subtree, and then the right subtree. The postorder traversal that prioritizes left before right is when you visit the left subtree, then the right subtree, and then the node itself. This has a recursive solution because the algorithm breaks down the traversal process by exploring the left and right subtrees of every node.

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/68bef3f2-5f08-43ef-97cc-ca845d43d89d)

- The first line is the base case that checks if the current node is null and returns if it is. This means that when the algorithm reaches a leaf node, it will first try and explore its left subtree and return since its left child is null. It will then use the leaf node itself in some way (printing in this implementation) and then try and explore the right subtree and return since it's also null. 
- The next lines execute the traversal part of the algorithm, recursively calling the function on the left child of the node first since this is an inorder implementation. The next line is printing the current node that the call stack is on. The final line recursively calls the function on the right child to explore the right subtree.
- For the preorder and postorder implementations, you would just need to switch the order in which you print the current node and recursively search its children. For preorder, you would print the value first, then recursively call the function on its left child, and then its right child. For postorder, you would recursively call the function on its left child, then its right, and then print out the current node's value.

#### Visualization of Inorder Traversal

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/d0ee3850-4650-418d-8e66-be8a6022ee48)

#### Visualization of Preorder Traversal

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/43f42d21-0a99-432d-8dd4-6f931c9634b9)

#### Visualization of Postorder Traversal

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/b25ee512-9568-4d20-81c9-6706090cdc7e)

#### Time Complexity

Since all we are doing is visiting every node, this algorithm has O(n) time complexity. However, if we were to apply DFS to a scenario like where we have to build a sorted array out of values given in random order without a binary search tree of those values already given, we would first have to build the binary search tree and then apply DFS to add them to the array. Building the tree would mean inserting n elements into the tree and since insertion into a binary search tree takes $\log{n}$ time, building the tree would take O($n\log{n}$) time. Then you have to add on the time it takes to apply DFS to put the elements into an array, taking O(n) time. Adding these two operations together, the time complexity for this scenario would be O($n\log{n} + n$) but since $n\log{n}$ grows much faster than n, we can treat the added time complexity of the DFS as a constant and disregard it, leaving the final time complexity as O($n\log{n}$). Another way to look at it is to look at an example of something we've already seen.
If the time complexity was O($2n\log{n}$) it would be the same as saying O($n\log{n} + n\log{n}$) and since we ignore constants when they multiply or add to variables, the time complexity simplifies to O($n\log{n}$). $n\log{n}$ is greater than n so since the time complexity of O($n\log{n} + n\log{n}$) simplifies down to O($n\log{n}$), then O($n\log{n} + n$) would also simplify down to O($n\log{n}$). In general, when there are time complexities where there are multiple different operations happening to a variable added together, we only care about the largest term because it would grow the fastest and it would simplify down to just the largest term for the same reasons as if it were multiplied by a constant. 

### Breadth-First Search

Breadth-first search (BFS) is a traversal algorithm for trees that traverses all nodes on the same level first before going down the tree to the next level, prioritizing breadth over depth. This is also called level-order traversal because we are going level by level down the tree. When traversing the tree using BFS, you usually go from left to right for each level so you would process the leftmost node from that layer first and end at the rightmost node, but if you want to do that for every level, you can't recursively call the function on the leftmost node's children if you end at the right node and want to maintain the same ordered traversal for the next level so recursion is not used for BFS. Rather, you can do it iteratively by maintaining a queue to keep track of which nodes to visit next. For any particular level, you would first process the leftmost node, add its children to the queue, and then move on to the next node in the level, which would automatically be the next in line in the queue and repeat the same process until the entire level has been processed. 

#### Implementation 

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/1fcbc30e-ff92-4077-8186-e01768d16667)

- The first line constructs the queue that will keep track of the nodes that have yet to be visited
- The next line checks if the root exists and pushes it to the queue if it does
- The next line makes a level variable to keep track of how many levels we have traversed
- The next lines are where the traversal happens. The while loop conditions checks for if the queue is nonempty, which would mean we still have elements to traverse.
    - First, it prints out the current level that is being traversed and initializes a length variable to keep track of the initial size of the queue before the level was traversed since the size changes after enqueuing and dequeuing during the traversal of that level. The for loop iterates the number of times equal to the length that was initialized.
        - The for loop first initializes a pointer that points to the current node being processed, which would be the first node in the queue
        - It then pops that element from the queue and prints out its value
        - Then there are two if-statements that check if that node had a left and right child. If it does have children, we would push it onto the queue, prioritizing the left child first since we want to traverse each level from left to right.
    - After the level has been fully traversed, it increments the level variable and goes to the next iteration of the while loop, which would be the next level of the tree

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/d40c5b62-5683-4cca-ad0d-6fa5292cb1b4)

#### Time Complexity

Similarly to bucket sort, even though we have a nested loop in the code, all we did was visit every node and perform a simple operation on each of them, which means it takes O(n) time. Technically, the time complexity is O($cn$) where c represents the number of operations you perform per node, but since this is a constant we can disregard it and the time complexity still comes out to be O(n). 

### BST Sets and Maps

Sets and maps, similar to stacks and queues, are interfaces that can be implemented using trees. Implementing them with trees allows for O($\log{n}$) time for operations. Sets are data structures that have unique elements and implementing them with binary search trees ensures that they are stored in order while still having O($\log{n}$) time for operations, unlike arrays where the operations take O(n) time. Maps are data structures that operate on key-value pairs. Each element is a key that has a value mapped to it. For example, a phonebook has a list of names sorted in alphabetical order. These are the keys. Each name has an associated phone number mapped to them, which serves as the value. The key-value pair in this example would be the name and corresponding phone number with that name. Implementing a map with a binary search tree also allows for O($\log{n}$) time for operations and ensures a sorted order, much like the alphabetized order in a phonebook. Each key could have any value mapped to it such as an integer, string, object, etc., and can also have multiple values associated with it.

Languages like Java and C++ have built-in TreeMaps but languages such as Python and JavaScript require you to import an external library to gain access to such data structures. Here is the declaration of a built-in TreeMap in C++:

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c5c5437c-03e5-403e-aee4-5250fc322cc0)

## Backtracking

### Tree Maze

The backtracking algorithm is similar to the DFS algorithm in that it searches each path of a leaf node using DFS to search for a particular solution to a given problem. This is usually a brute-force approach when there is no other efficient way of doing it. 

#### Example Problem
An example of an application for backtracking is finding a path from the root to a leaf node that does not contain a 0 in it. For this problem, we would be running the algorithm on a binary tree instead of a binary search tree. You would use DFS to search each path to a leaf node until you reach a zero or find a path to a leaf node without a 0 in it. If the current path being searched has a 0 in it, the algorithm will backtrack to another path that was skipped earlier on in the decision tree. This is similar to a maze where you go in a certain direction or path until you hit a dead end, at which point you backtrack to other possible paths you could have taken until you reach the end of the maze. Since we are using DFS to traverse the tree, we will have to use a recursive solution, which means we need at least one base case. For this problem, there are a couple base cases. The first is if the tree is empty, meaning there is no root node, or the root node is 0 since that would mean that there are no possible paths that don't contain 0. The second is if you have reached a leaf node that was nonzero without returning false up to that point, you can return True to signify that you have found a path to a leaf node without 0 since if you did reach a node in the path with 0, you would've returned False and backtracked to another path. 

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/48ac00f5-1eb6-4c1b-9f95-497a72b7584a)

- The class at the top is an implementation of the binary tree node
- The first if-statement for the backtracking function covers the first base case where the root is either null, meaning the tree is empty, or if the root node's value is 0, returning False if either is true
- The second if-statement covers the second base case that checks whether the current node is a leaf node by checking if both children are null, returning True if it is a leaf node
- The next two if-statements implement the DFS traversal portion of the algorithm, recursively calling the function on the left child, then the right child to see if either the left or right subtrees contain a path to a leaf node without a 0 in it
- The return statement at the end returns false since if we reached a leaf node that contained 0, it would get past the two recursive calls on its children and we would want to return false in this case since there is a 0 in the path

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/102f4676-b7f4-4cc3-b5fd-8eec9f993155)

#### Variation of the Problem

If the problem instead asked to fill an array of all the values of the nodes in a valid path instead of just returning a boolean, we would have to alter the solution a bit. 

#### Implementation of Array Variation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/4fa4eda2-4624-4210-a509-df2c54fd9d1f)

- The code will be mostly the same except we pass in a path array that will allow us to keep track of the values of the current path we are traversing and will be the same array that will have the values of a valid path without 0's in it if one exists
- The return value of the function is still a boolean because that will allow us to tell when the algorithm should backtrack and when there is a valid path or not
- The first if-statement is the same, checking the first base case
- The next line adds the root node to the path because if it passed the base case in the lines before, the root node will always be a valid node in the path and thus can be added to the path array
- The next if-statement checks for the second base case
- The next two if-statements are the same as before, recursively traversing the tree to see if there is a valid path
- The next line pops the latest element from the array since if it passes through the previous two if-statements that traversed the tree, it means that the path was invalid and the current node of that iteration of the recursion needs to be removed from the array. The path would be invalid because if it wasn't, it would've returned True all the way up the call stack to the root node and it would never go down to this line to pop the nodes. This also means that if both the left and right subtrees of the root node have been traversed and the algorithm moves onto this line, that means both subtrees have returned false and it will pop the root node off the array, signifying that there is no valid path that exists in the tree.
- The last line is the same return statement as the previous implementation, returning false in case a leaf node containing 0 existed and it was not caught earlier

#### Visualization of Array Variation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/56ff08ff-548e-4299-a46f-e84f4d14b630)

#### Time Complexity

Since in the worst case we would have to traverse through the entire tree to find a valid path, the time complexity of this algorithm would be O(n). This is usually the case for backtracking algorithms since it is meant to be a brute-force approach and is meant to run over all possibilities of the problem. In this case, it would be all possible paths of the tree.

## Heap / Priority Queue

### Heap Properties

Heaps/Priority Queues are the same type of data structure. They are ordered and complete binary trees where each node's descendants all have values greater than it or less than it depending on if it is a min heap or max heap. Heaps are sometimes called priority queues because values will be put into a queue-like order when being added or removed and are prioritized based on their relative value, which is being smaller or larger. Heaps need to maintain two properties: structure and order. The structure property comes from the fact that they have to be complete binary trees, meaning that each level has to be full of nodes excluding the bottom level. This also means that the bottommost level has to be completed before adding children to any of the bottom-level nodes. The order property is the way in which values are prioritized. Unlike binary search trees, heaps can have duplicate elements. In a min heap, smaller values have more priority, meaning that they will be the first ones out, and each node's descendants will all be greater than or equal to it. In a max heap, larger values have more priority and each node's descendants will be less than or equal to it. In this section, we are going to focus on min heaps.

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/e00baae9-fc06-4061-bf68-b44a72444759)

Even though heaps are visually represented as binary trees, they are implemented using arrays rather than nodes and pointers. Elements in the array also start at index 1 rather than index 0. This is because it makes it easier to travel to the children or parent of a given node. Using a few formulas, you can jump from a parent node to either of its children or from a child node to its parent. 
- $leftChild = 2i$
- $rightChild = 2i + 1$
- $parent = i/2$

i is the index of the node you are at. This will always be the case because the heap is a completed tree so there won't be any holes in any level. If it weren't a complete tree, some indices may not have an element and you would be trying to access a null element if there was a hole in that index. The contiguous structure of arrays also fits well for this structure since the completeness ensures that there aren't these types of holes and instead the elements are stored one after another. This is also why the root node is at index 1 instead of 0 because the formulas wouldn't work on the root node if it started at 0. Elements in the array are arranged in the same order as they would be searched in BFS (level by level, left to right). Dividing by 2 takes you from one node to its parent because in either case, whether it is a left or right child, dividing both equations by 2 results in you being at the parent index i. If you are at a right child, dividing the entire expression by 2 cancels out the 2 in $2i$ and $1/2$ truncates down to 0, resulting in you being at index $i + 0 = i$. 

#### Visualization of Heaps

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/19080b80-4d03-43eb-91c7-2d0b8e766d2d)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/6f8a2ec0-d10a-4f56-bd66-901dc72fc979)

#### Visualization of Going From One Node to its Children and Parent

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c034d53f-8be1-41d9-b538-3297635b10b0)

### Push and Pop

#### Push
Pushing an element onto a heap includes pushing the element into the end of the array so that it first gets inserted into the last level, preserving the structure property, and continuously swapping the element with its parent until the order property is preserved. This process of repeatedly swapping the elements with another node is called percolating. In this case, we are percolating up since we are swapping the nodes with their parents. 

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/dece080b-5a92-452f-ae53-0db2536b584d)

- The first line pushes the element to the end of the array
- The next line initializes the index i to be at the same index that the element was pushed to
- The while loop is where the percolation occurs. The loop condition if i is greater than 1 and if the element that was pushed is smaller than its parent. Index i has to be greater than 1 because if i was 1, dividing by 2 would truncate it down to 0, which is an invalid index for heaps since we ignore that position.
    - The percolation algorithm starts by swapping the pushed element with its parent
    - It then divides i by 2 using integer division so that it points to the new index of the pushed element
 
#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/67b8c928-c80a-4a0c-b1ee-ec4757ba085e)

#### Pop

Popping involves removing and replacing the element at index 1 with the last element in the array and percolating it down with the minimum of its two children until the order property is maintained. If you were to just pop the first element off and replace it with the minimum of its two children and repeat this process for each of the replacement nodes, you would be introducing a hole in the last level you took an element from, which would violate the structure property of heaps. 

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/bb97ef34-2f89-4885-987a-8bb50727daba)

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/98147b23-da3e-4197-97bf-67fe93b6dea8)

- The first if-statement checks if the heap is empty. The heap would be empty if the array was of size 1 instead of size 0 because the zeroth index is not used in the heap but still counted in the array size.
- The next if-statement checks if the heap is only 1 node and pops and returns it if so
- The next few lines save the root node, replace the root node with the last node, pop the last node off the array, and initializes the index i to 1.
- The while loop is where the downward percolation occurs. The condition checks if the current node has a child to percolate to. It checks specifically for the left child because it can't have a right child without a left child because of the complete structure property. If there was a right child without a left child, that would create a hole in that level.
    - There are three cases to consider for the percolation process: if the current node needs to swap with the right child, the left child, or no swap is needed and it is in the correct position. If it has both children, you choose to percolate down the path that has the minimum value of the two children. If the current node only has a left child then you just compare the current node with its child and swap them if needed. If the current node has no children, the element is where it needs to be and the percolation ends. This is automatically checked in the while loop condition. 
    - The first if-statement checks three conditions and covers case 1. It checks if the right child exists, if the right child has a smaller value than the left child, and if the current node's value is greater than the right child. If all of these conditions are met, it will choose to percolate down the right path and swap with the right child. It will also update i to point at the right child's index.
    - The second if-statement checks if the current node's value is less than the left child, covering the second case. If this condition is satisfied, it swaps with the left child and updates i to point at that index.
    - The else statement takes care of case 3 when the current node's value is smaller than both its children's values. In this case, it means that the current node is already in the correct position and thus the program breaks from the while loop. This also executes if it only has the left child and is smaller than it.
- Once the while loop is finished, that means the replacement node is in the correct position and it returns the original root node

#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/ea3f645b-13ef-49fd-867b-e8ed1351151e)

#### Time Complexity

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/c5d5631f-a913-4593-9f68-f98676b7f028)

Getting the min/max of the heap is basically just accessing the root node and access in an array takes O(1) time so the time complexity of getting the min/max of the heap is also O(1). The time complexity for both push and pop would be O($\log{n}$) because in the worst case for both, you would have to percolate through the entire height of the tree and since the tree is always balanced, the height will always be $\log{n}$. 

### Heapify

Heapify, or build heap, is an algorithm that constructs a heap given a list of values. If you were given an array of values in a random order, heapifying it would turn the array into a min/max heap. The heapifying process first involves moving the element at the zeroth index to the end of the array so that the index is basically ignored and all elements are now in a valid index of the array. Then the algorithm percolates the first half of the array down until they are in the correct position to preserve the order property of a heap. You only have to percolate the first half of the nodes because the other half will not have any children, so they are already in the correct position relative to the others. 

#### Implementation

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/10821f09-9bc6-408f-baee-c46c5f6cd71b)

- The first line moves the element in the zeroth index to the end of the array
- The next couple of lines initialize the heap and an integer that will point to the last index of the first half of the array because that is where the first non-leaf node will be. This cur index also helps keep track of which node we are currently percolating.
- The outer while loop runs the percolation process for every node in the first half by checking if the cur index is greater than 0
    - The next line initializes an index i to keep track of the index of the current node during the percolation process
    - The inner while loop checks if the current node has a left child to verify that it has a path to possibly percolate down. This section of code is the same as the code in the pop function that percolates the nodes down.
    - After the percolation process is done, cur is decremented and the algorithm moves on to the next node to be percolated
 
#### Visualization

![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/e835a3bb-db97-4e18-8b7c-bf7b53560629)

#### Time Complexity

If there are n nodes in the binary tree, then there are roughly $\frac{n}{2}$ leaf nodes in the tree so we can determine how many levels each node has to percolate down and how much work is done during each node's percolation. Half of the nodes are leaf nodes because heaps are always going to be complete binary trees, meaning that the last level will always be full of leaf nodes and if the last level is full, that means that half of the tree is full of leaf nodes. However, this is true for any heap/complete binary tree. Because the number of nodes doubles each level, the last level is always going to dominate the total number of nodes in the tree, being greater than or equal to the sum of all nodes in every previous level. Going up from the last level, the next lowest level only has to percolate down one level. The next level has to percolate down two and so on, with the root node having to percolate down the entire height of the tree. Percolating down the tree is better than percolating up because there are fewer nodes that have to travel the height of the tree. Percolating down means only the root node would have to travel the entire height, but if you percolated up, you would have to percolate the entire bottom level up the height of the tree. Although the number of nodes that have to percolate decrease as you go up a level, the number of levels those nodes have to percolate increase. This can be encapsulated in a summation formula that will come out to O(n). 

- For the last level, you would not need to percolate them since they are leaf nodes so you would be percolating $\frac{n}{2}$ nodes 0 times. The next lowest level would have half of those nodes and would need to percolate down 1 level, so the total number of operations would be $0 * \frac{n}{2} + 1 * \frac{n}{4}$
- This pattern will continue, with the incrementing coefficient representing the number of levels you have to percolate down and the number of nodes halving each time so the total number of operations would look like $0 * \frac{n}{2} + 1 * \frac{n}{4}... + h * 1$ where h is the height of the tree
- This can be encapsulated into a summation:

$\frac{n}{4} \displaystyle\sum_{k=1}^{h} \frac{k}{2^{k-1}}$ 

- n is the total number of nodes in the heap
- k is the number of levels you have to percolate down
- h is the height of the tree
- The coefficient of the summation is $\frac{n}{4}$ because that's how many nodes you have to percolate down for the second to last level. The numerator is k because that's how many times you have to percolate down at any given level. The denominator is $2^{k-1}$ because each level up is half the number of nodes as the level below so the $\frac{n}{4}$ out in front of the summation gets reduced by $2^{k-1}$ depending on what level you are at. Since the series converges to a value, 1, the time complexity would be O($\frac{n}{4}$) and this simplifies down to O(n).

#### Alternative Proof

The formula to calculate the maximum number of nodes at any given height h is $\lceil\frac{n}{2^{h+1}}\rceil$ where n is the number of nodes in the heap. The time complexity of heapifying a node at height h is O(h) (this assumes that the height is measured from the bottom upward and the bottom level starts at height 0). Therefore at any given level of height h, the number of operations performed is $\lceil\frac{n}{2^{h+1}}\rceil * O(h)$. 
- The total number of operations for heapifying the entire tree is

$\displaystyle\sum_{h=0}^{\log{n}} (\lceil\frac{n}{2^{h+1}}\rceil * O(h))$

- You can break this down and rewrite it as

$\displaystyle\sum_{h=0}^{\log{n}} (\lceil\frac{n}{2^{h} * 2}\rceil * c * h)$

because in Big-O notation you can ignore any arbitrary constant c so rewriting O(h) as c * h allows us to pull out all constants and rewrite the entire expression as

$\frac{c * n}{2} * \displaystyle\sum_{h=0}^{\log{n}} \frac{h}{2^h}$

- This is less than the infinite series

$\displaystyle\sum_{h=0}^{\infty} \frac{h}{2^h}$

because this series is adding more terms and all terms are positive.

- This infinite series converges to 2 so the total time complexity of heapifying the entire tree is

$O(\frac{c * n}{2} * 2) = O(c * n) = O(n)$
