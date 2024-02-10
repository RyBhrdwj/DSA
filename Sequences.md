<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sequences</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h2 id="subarray">Subarray</h2>
<p>A subarray / substring is a <strong>contiguous part</strong> of array / string that maintains relative ordering of elements. All subarrays can be generated iteratively.<br>
<em>TC : O(N<sup>3</sup>)</em></p>
<pre><code>for (int idx = 0; idx &lt; n; idx++)
{
	for (int jdx = idx; jdx &lt; n; idx++)
	{
		for (int ptr = idx; ptr &lt;= jdx; ptr++)
		{
			// Operations Here
		}
	}
}
</code></pre>
<ul>
<li><a href="https://leetcode.com/problems/palindrome-partitioning/submissions/1170563466/">Palindrome Partitioning</a></li>
</ul>
<h2 id="subsequence">Subsequence</h2>
<p>A subsequence maintains relative ordering of elements but <strong>MAY or MAY NOT be contiguous</strong>.</p>
<h2 id="subset">Subset</h2>
<p>A subset <strong>MAY NOT</strong> maintain relative ordering of elements and <strong>can or can’t</strong> be a contiguous part of an array.</p>
<h2 id="combination">Combination</h2>
<p>Two combinations are unique if the frequency of at least one of the chosen numbers is different.</p>
<p>Above patterns can be generated using <strong>Backtracking</strong> by making <strong>take / not - take</strong> choice for every element.<br>
<em>TC : O(2<sup>N</sup>)</em></p>
<pre><code>recursion()
{
	if (Base Case) return;
	
	// Take
	recursion();
	
	// Don't take
	recursion();
}
</code></pre>
</div>
</body>

</html>
