# Identification
- Array Question
- O(N<sup>2</sup>) Brute Force where inner loop variable is dependent on outer one.
```cpp
// jdx -> [i to n], [n to i], [0 to i], [i to 0]
for (int i = 0; i < n; i++)
    for (int jdx = i; jdx < n; jdx++)
```

