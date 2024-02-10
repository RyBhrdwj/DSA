## Subarray
A subarray / substring is a **contiguous part** of array / string that maintains relative ordering of elements. All subarrays can be generated iteratively.
 *TC : O(N<sup>3</sup>)*
```
for (int idx = 0; idx < n; idx++)
{
	for (int jdx = idx; jdx < n; idx++)
	{
		for (int ptr = idx; ptr <= jdx; ptr++)
		{
			// Operations Here
		}
	}
}
```

- [Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/submissions/1170563466/)

## Subsequence
A subsequence maintains relative ordering of elements but **MAY or MAY NOT be contiguous**.

## Subset
A subset **MAY NOT** maintain relative ordering of elements and **can or can't** be a contiguous part of an array.

## Combination
Two combinations are unique if the frequency of at least one of the chosen numbers is different.

Above patterns can be generated using **Backtracking** by making **take / not - take** choice for every element.
*TC : O(2<sup>N</sup>)*

```
recursion()
{
	if (Base Case) return;
	
	// Take
	recursion();
	
	// Don't take
	recursion();
}
```
