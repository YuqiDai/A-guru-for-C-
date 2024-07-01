# C/C++ in memory space
## 1. Generic layout
For a program, it can only manipulate the virtual memory space then OS help map the virtual memory address of a program to the corresponding physical memory address. The diagram below shows the generic virtual memory layout of a C/C++ program.    
*And need to notice that the two sample diagrams are based on the virtual memory space layout of the Linux 32-bit system*.

![Generic layout](./resource/Memory%20layout%20of%20C++/memory-layout-in-c.png)

Components:    
1. Code segement
2. Initialized data segment (aka: data segment)
3. Uninitialized data segment (aka: BSS -> block started by symbol)
4. Heap
5. shared space between stack and heap
6. Stack
7. Cmd arguments

In practical, there is a small entry point program under code segment which is used to activate the program. And there's a block of environment variables above cmd arguments block. As shown below:   

![linux32bit](./resource/Memory%20layout%20of%20C++/linux32bit.png)

## 2. Abstract layout
As saying as an abstract layout, there are five blocks:     
stack, heap, static, const, free store.    

Attention!
* Free Store    
The free store is one of the two dynamic memory areas, allocated/freed by new/delete. Object lifetime can be less than the time the storage is allocated; that is, free store objects can have memory allocated without being immediately initialized, and can be destroyed without the memory being immediately deallocated. During the period when the storage is allocated but outside the object's lifetime, the storage may be accessed and manipulated through a void* but none of the proto-object's nonstatic members or member functions may be accessed, have their addresses taken, or be otherwise manipulated.    

* Heap    
The heap is the other dynamic memory area, allocated/freed by malloc/free and their variants. Note that while the default global new and delete might be implemented in terms of malloc and free by a particular compiler, the heap is not the same as free store and memory allocated in one area cannot be safely deallocated in the other. Memory allocated from the heap can be used for objects of class type by placement-new construction and explicit destruction. If so used, the notes about free store object lifetime apply similarly here.
 

