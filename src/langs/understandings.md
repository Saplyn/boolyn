# Understandings

## Variable, Function, and Program

- Variable is the container of data.
- Function is the container of instructions.
- Program is the honestest way to instruct computers. It describes how states are manipulated, and how instructions are carried out.

## Memory: Stack and Heap

Stack is a segment of memory that is used to store local variables and function
call information of one thread. A new stack frame (a contiguous chunk of
memory) is created (push) each time a function is called, and destroyed (pop)
when returns. Values live on the stack become invalid when its stack frame is
destroyed.

Heap is a pool of memory used for dynamic memory allocation. It allows us to
allocate a block of memory of a given size and get a pointer to it, the
allocated memory stays reserved until it is explicitly deallocated. Values
live on the heap are valid until deallocated. The heap is shared among all
threads.
