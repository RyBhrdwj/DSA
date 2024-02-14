
# Description
- LIFO
- Implemented using linked list
- push, pop, size, empty - O(1)
- Vector vs Stack
	- Search takes O(1) in vector using indices but stack takes O(N)
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
- O(N<sup>2</sup>) Brute Force where inner loop variable is dependent on outer one.
```cpp
for (int i = 0; i < n; i++)
    for (jdx dependent on i)
```

