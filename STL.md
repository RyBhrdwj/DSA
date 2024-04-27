# Functions

minmax() : returns pair with min and max element

ceil() : returns the smallest integer > value (eg. ceil(1.1) = 2)
floor() : returns the largest integer < value (eg. floor(-1.9) = -2)

![image](https://github.com/RyBhrdwj/DSA/assets/95015767/5bca4047-a83d-48a1-bf64-9106eebb9cd3)

## Binary Search
- Both functions take upto 4 arguments
    - all(v)
    - Target element
    - Predicate function*

- If the element > last element then `v.end()` is returned

- lower_bound() : returns iterator to `element >= target`

- upper_bound() : returns iterator to `element > target`



# Vector

minmax_element() -> returns min & max element in pair

# String

substr() : Takes starting index and length of substring

- substr(idx) : substr from idx to end
- substr(idx, len) : substr `[idx, idx + len)`
