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
![image](https://github.com/TenHam3/Arrays-Notes/assets/109705811/1ba56d74-30eb-4278-be31-1effb1e7fc92)
- The elements stored are integers, which take 4 bytes to store in memory so the addresses increment by 4
![image](https://github.com/TenHam3/Arrays-Notes/assets/109705811/e2e1e7de-8d46-420b-aa12-43a5b0cc9934)
- The elements stored here are characters, which only take 1 byte to store in memory so the addresses increment by 1

### Static Arrays

Static Arrays are fixed size arrays that cannot resize when adding or removing values, resulting in the drawback of not being able to add or remove as many values as you want

- Since arrays are contiguous blocks of memory, adding an element when the array has reached maximum capacity does not work with static arrays because there is no guarantee that the next block of memory is available to allocate another element
  - Because of the index system of arrays, adding another element somewhere else in the RAM not adjacent to the array will most likely result in the wrong data being accessed as the operating system will try and access the element you added by going to the index after the last element in the array, which may contain some other data
- Reading/Writing to the ith element takes O(1) time because the indexing system allows the operating system to instantly access the ith element
- Insertion/Removal from the end of the array takes O(1) time because the indexing system allows you to instantly write to the last element via its index (removing would mean replacing it with a placeholder value such as 0)
- Insertion/Removal from the middle takes O(n) time because you may have to shift every element in the array before/after inserting/removing an element (this would happen if you were to insert/remove from the beginning of the array)
![image](https://github.com/TenHam3/Arrays-Notes/assets/109705811/3da3b013-0d22-4279-b7a0-2cb69e3962df)


### Dynamic Arrays

Dynamic Arrays are dynamically sized arrays that resize themselves if you add an element when at full capacity or remove an element at low capacity
- It does this by reconstructing a new array that is typically double the size of the original array and copying all the original elements from that array into the new one and freeing the memory that the old array was taking up. It then adds/removes the element the user wanted to before resizing
- The doubling in size makes pushing/popping an element take O(n) time on average because you wouldn't have to keep reconstructing the array after every push/pop
  - The amount of operations it takes to reconstruct an array by doubling is always dominated by the most recent reconstruction, meaning that the amount of operations it takes to reconstruct an array is always greater than or equal to the sum of the amount of operations it took from previous reconstructions. This also means the total sum of all operations it took to reconstruct the array into the latest size is less than or equal to twice the amount of operations the latest reconstruction took
    - Pushing an arbitrary n number of elements takes O(2n) time, which reduces to O(n) time
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/cac0fe9f-f7cb-4c30-896b-fd1e8167fc85)

- Time complexity for each operation is the same for dynamic arrays as they are for static arrays

### Stacks

Stacks are LIFO (Last In First Out) data structures that support three operations: push, pop, and peek.
- Push adds an element to the "top" of the stack, or the end of the data structure you implement it with
- Pop removes an element from the top of the stack
- Peek accesses/reads the element at the top of the stack but doesn't remove it
- All these operations take O(1) time, which means stacks can be implemented using dynamic arrays since dynamic arrays support all these operations with the same time complexity
![image](https://github.com/TenHam3/Data-Structures-and-Algorithms-Notes/assets/109705811/51ae01a4-7015-450b-9c84-0f89e4bde47a)

- Stacks require a pointer or some way to keep track of the number of elements in the stack so you can maintain where the "top" of the stack is and know where to push/pop/peek the next element
- Stack operations only work on the topmost element so you cannot add, remove, or access elements from the middle of the stack
- A common analogy is imagining a stack of plates, where it is easy to add or remove plates from the top, but trying to add or remove plates from the middle or bottom is harder so you only do such operations on the top

## Linked Lists
### Singly Linked Lists
