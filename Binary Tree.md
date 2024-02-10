# BFS (Level Order)
It is performed using a **queue**.
Add root to queue, while queue isn't empty traverse it and add children of every node to the queue. 

# Recursive DFS

Order of Traversal is determined by placement of logic / operations in relation to recursive calls.

```cpp
void helper(TreeNode* root)
{
	// preorder
	helper(root -> left);
	// inorder
	helper(root -> right);
	// postorder
}
```

# Iterative DFS

![DFS Visualization](https://i.stack.imgur.com/FFWk3.png)

## Generic Method
Store every node with their state which signifies their order during traversal.
PreOrder	: go to left child
InOrder	: go to right child
PostOrder: remove node from stack 

```cpp
stack<pair<TreeNode*, int>> stk;
stk.push({root, 0});

while (not empty)
{
	// Store pair & state by reference
	auto& top = stack.top();
	auto root = top.first;
	int& state = top.second;
	
	// Add root's value to result depending on order.
	
	if (0) push left child; 	// preorder
	else if (1) push right child;	// inorder
	else stk.pop(); 		// postorder
}
```

## PreOrder

Put parent in result, add right child to stack and go to left child.
If no left child, go to nearest right child i.e **stack.top()**
```cpp
while (root || !stk.empty())
{
    if (root)
    {
	preorder.push(root);
	if (right) stk.push(right);
	root = root -> left;
    }
    else
    {
        root = stk.top();
        stk.pop();
    }
}
```

## InOrder

Add parent to stack and go to left child.
If no left child, go back to parent, put it in result and go to right child.
```cpp
while (root || !stk.empty())
{
    if (root)
    {
		stk.push(root);
		root = root -> left;
    }
    else
    {
        root = stk.top();
        inorder.push(root);
        root = root -> right
        stk.pop();
    }
}
```

## PostOrder

# Morris Traversal
