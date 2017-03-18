# Vector

## What is vector?
Vector is a `dynamic arrary` in C++ STL. It allows us to find an element with
O(1), append or remove last element average complexity is O(1) and delete
random element with O(N).

# How
Vector uses a technique named `Double Array`.
* If my array is not full, we add new element at end of array.
* If my array is full:
  + Allocate an new memory = 2 * Length of current array
  + Copy current array to new array.
  + Append new element to new array.
