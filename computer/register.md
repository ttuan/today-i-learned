A register is a small amount of storage on the CPU and is the fastest method for
a CPU to access data.

There are 8 purpose registers:
* EAX: *accumulator register* store return values from function calls. (+, -)
* EDX: *data register* extension of EAX register, store extra data for mor
    complex caluculation like * and /
* ECX: *count register* for loop operations. ECX counts downward, not upward.
* ESI: *source index* source index for the operation and holds the location of
    input data stream.
* EDI: *destionation index* points to the location where the result of data
    operation is stored.
* ESP: *stack pointer* where store arguments of a function, point to the very
    top of the stack.
* EBP: *base pointer* points to the bottom of the call stack.
* EBX: the only register that was not designed for anything specific, is used
    for extra storage.
