# Description
- LIFO
- Implemented using linked list
- push, pop, size, empty - O(1)
- Vector vs Stack
	- Search takes O(1) in vector using indices but stack takes O(N)
	- Vector takes amortized O(1) to resize but stack resizes in O(1)

# Implementation

```cpp

```

# Identification
- O(N<sup>2</sup>) Brute Force where inner loop variable is dependent on outer one.
```cpp
for (int i = 0; i < n; i++)
    for (jdx dependent on i)
```

