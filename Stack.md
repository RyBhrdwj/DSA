
# Description
- LIFO
- Implemented using linked list
- push, pop, size, empty - O(1)
- Vector vs Stack
	- Access takes O(1) in vector using indices but stack takes O(N)
	- Vector takes amortized O(1) to resize but stack resizes in O(1)

# Implementation

The start of linked list would represent the top of stack.

Push -> make a new node & point it to top.

Pop -> if not empty, delete top and update it to next node.

```cpp
class Node 
{
    int data;
    Node *next;

public:

    Node(int x) 
    {
        data = x;
        next = nullptr;
    }
    
    Node(int x, Node *next)
    {
        data = x;
        this -> next = next;
    }
};

class Stack 
{
    int size;
    Node *back;

public:

    Stack() 
    {
        size = 0;
        back = nullptr;
    }

    void push(int x) 
    {
        Node *node = new Node(x, back);
        size++;
    }

    void pop()
    {
        if (!size) return;

        Node *temp = back;
        
        back = back -> next;
        size--;
        
        delete temp;
    }

    int top()
    {
        if (!size) return;

        return back -> data;
    }

    bool empty()
    {
        return !size;
    }
};
```

# Identification

- If the problem requires LIFO traversal, like iterative dfs.

- **[MONOTONIC STACK PROBLEM]**<br>
O(N<sup>2</sup>) Brute Force where inner loop variable is dependent on outer one.<br>
Next, identify whether the problem is to find the next smallest / greatest and then the direction.

```cpp
for (int i = 0; i < n; i++)
    for (jdx dependent on i)
```

## 1. Next Greatest / Smallest Element to Right

Example : [2, 3, 1, 4] --- NGR ---> [3, 4, 4, -1]

Only smaller values get popped as current is greater than them.

- ALGORITHM
	- Traverse stack in the direction from that side's end to other end<br>
    Ex. Next Greatest to right -> Traverse `N-1 -> 0`
		- If empty stack, `put -1`
		- Else `top > curr ? top : stk.pop()`
		- Push current in stack

Different condition would be used for next smallest

## 2. Next Greatest / Smallest Element to Left

Same as the above, just slight modifications due to different direction of traversal.

# Questions


- [Stock Span](https://leetcode.com/problems/online-stock-span/)
- [Largest Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [Max Rectangle](https://leetcode.com/problems/maximal-rectangle/)
- [132](https://leetcode.com/problems/132-pattern/)
