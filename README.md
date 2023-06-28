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

### Stacks
