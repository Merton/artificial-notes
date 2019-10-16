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

### Asymptotic Order of Growth
Let’s assume we have two algorithms A1 and A2 for a given problem, and their run-time is given by f1 for A1 and f2 for A2, where:

𝑓<sub>1</sub>(𝑛)=0.00001×2<sup>𝑛</sup>

𝑓<sub>2</sub>(𝑛)=289346724587138654380×𝑛<sup>2</sup>

For small data, A1 is faster, but eventually, for big enough data A2 is faster.  We are interested in the behaviour of algorithms as the input data grows large.

## O Notation
O notation provides an asymptotic upper bound on a function

We write 𝑓(𝑛) ∈ 𝑂(g(𝑛)) if there are positive constants 𝑛<sub>0</sub> and 𝑐 such that for n>𝑛<sub>0</sub>, 𝑓(𝑛)≤𝑐(𝑔(𝑛)) 

![image](https://user-images.githubusercontent.com/25505506/66656905-c6404280-ec36-11e9-8fd4-98a9168a0695.png)

## Ω Notation
Ω notation bounds a function from below

![image](https://user-images.githubusercontent.com/25505506/66658299-1f10da80-ec39-11e9-89c6-42b056d91dd9.png)

## Θ Notation
Θ notation asymptotically bounds a function from above and below.

We write 𝑓(𝑛)∈𝜃( 𝑔(𝑛)) if there are positive constants 𝑛<sub>0</sub>, 𝑐<sub>1</sub> and 𝑐<sub>2</sub> such that for n>𝑛<sub>0</sub>, 𝑐<sub>1</sub>(𝑔(𝑛))≤𝑓(𝑛)≤𝑐<sub>2</sub>(𝑔(𝑛)) 


![image](https://user-images.githubusercontent.com/25505506/66658400-4e274c00-ec39-11e9-9f85-934394e18750.png)

## O Notation or Θ Notation
O Notation is often used informally to describe tight asymptotic bounds.
We will use this informal convention of using O Notation to refer to a fairly tight asymptotic upper bound on the running time of an algorithm – even though Θ notation is more strictly correct.

Another common abuse of the notation you will see in text books (and in lecture notes) is to say f(n) = O(g(n)) rather than f(n)∈O(g(n))


# Space Complexity
How much memory will my program need? Does algorithm A use less memory than alogrithm B
The space complexity of an algorithm A:X -> Y for input x is the number of memory cells it takes to execute A(x)

For a fixed notion of size, then a space bound of A:X-> Y is any function:
```
space: N -> N
```

You cannot use more space than time, as it takes time to write to space.

Therefore for all A:X -> `SPACE(A) ⊑ TIME(A)`

