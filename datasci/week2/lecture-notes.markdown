# Algorithmic Complexity

## Comparing algorithms
### Time Complexity
How long will my program take to run? Is algorithm A faster than algorithm B?

How does the runtime of an algorithm depend on the inputs

We can define a time bound for an algorithm A:X->Y as any function:
```
time: N -> N

Such that for all x ∈ X: the run-time of A(x) <= time(size(x))
```

### Space Complexity
How much memory will my program need? Does algorithm A use less memory than alogrithm B

### Communication Complexity
How packets will my algorithm send over the network? Is it less than B


### Constant-time 
```python
def myfunc(alist):
  ans = alist[0]**2
  print("The answer is", str(ans))
```
The length of time to complete does not depend on the size of the input. It is a 
constant-time function, therefore the run-time is of the order of 1: O(1)

Because the time is independent to size of the list as it just uses the first item.


### Iterations: Linear Time
```python
def myfunc1(alist):
  for thing in alist:
    print(thing)
```

Problem size is equal to the length of the list, the length of the run time is linearly dependent
on the size of the list. If the length is doubled the time taken will double. Therefor the order is n, or O(n).

### Nested Iterations: Quadratic time
```python
def myfunc2(alist):
  for thing1 in alist:
      for thing2 in alistL
          print(f"A pair is: {thing1}, {thing2}")
```

The length of time has a quadratic relationship with the length of the input, if the list doubles the run-time
will quadruple. This is O(n<sup>2</sup>).


## Do Constants matter?
  | n | nlogn | n2 | n3 | 1.5n | 2n | n!
-- | -- | -- | -- | -- | -- | -- | --
n=10 | <1s | <1s | <1s | <1s | <1s | <1s | 4s
n=30 | <1s | <1s | <1s | <1s | <1s | 18m | 1025y
n=50 | <1s | <1 | <1s | <1s | 11m | 36y | long
n=102 | <1s | <1s | <1s | 1s | 12892y | long | long
n=103 | <1s | <1s | 1s | 18m | long | long | long
n=104 | <1s | <1s | 2m | 12d | long | long | long
n=105 | <1s | 2s | 3h | 32y | long | long | long
n=106 | 1s | 20s | 12d | 31710y | long | long | long
