<h1 id="bfs-level-order">BFS (Level Order)</h1>
<p>It is performed using a <strong>queue</strong>.<br>
Add root to queue, while queue isn’t empty traverse it and add children of every node to the queue.</p>
<h1 id="recursive-dfs">Recursive DFS</h1>
<p>Order of Traversal is determined by placement of logic / operations in relation to recursive calls.</p>
<pre class=" language-cpp"><code class="prism  language-cpp"><span class="token keyword">void</span> <span class="token function">helper</span><span class="token punctuation">(</span>TreeNode<span class="token operator">*</span> root<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token comment">// preorder</span>
	<span class="token function">helper</span><span class="token punctuation">(</span>root <span class="token operator">-</span><span class="token operator">&gt;</span> left<span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">// inorder</span>
	<span class="token function">helper</span><span class="token punctuation">(</span>root <span class="token operator">-</span><span class="token operator">&gt;</span> right<span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token comment">// postorder</span>
<span class="token punctuation">}</span>
</code></pre>
<h1 id="iterative-dfs">Iterative DFS</h1>
<p><img src="https://i.stack.imgur.com/FFWk3.png" alt="DFS Visualization"></p>
<h2 id="generic-method">Generic Method</h2>
<p>Store every node with their state which signifies their order during traversal.<br>
PreOrder	: go to left child<br>
InOrder	: go to right child<br>
PostOrder: remove node from stack</p>
<pre class=" language-cpp"><code class="prism  language-cpp">stack<span class="token operator">&lt;</span>pair<span class="token operator">&lt;</span>TreeNode<span class="token operator">*</span><span class="token punctuation">,</span> <span class="token keyword">int</span><span class="token operator">&gt;&gt;</span> stk<span class="token punctuation">;</span>
stk<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">{</span>root<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">while</span> <span class="token punctuation">(</span><span class="token operator">not</span> empty<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token comment">// Store pair &amp; state by reference</span>
	<span class="token keyword">auto</span><span class="token operator">&amp;</span> top <span class="token operator">=</span> stack<span class="token punctuation">.</span><span class="token function">top</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token keyword">auto</span> root <span class="token operator">=</span> top<span class="token punctuation">.</span>first<span class="token punctuation">;</span>
	<span class="token keyword">int</span><span class="token operator">&amp;</span> state <span class="token operator">=</span> top<span class="token punctuation">.</span>second<span class="token punctuation">;</span>
	
	<span class="token comment">// Add root's value to result depending on order.</span>
	
	<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span> push left child<span class="token punctuation">;</span> 		<span class="token comment">// preorder</span>
	<span class="token keyword">else</span> <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> push right child<span class="token punctuation">;</span>	<span class="token comment">// inorder</span>
	<span class="token keyword">else</span> stk<span class="token punctuation">.</span><span class="token function">pop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 				<span class="token comment">// postorder</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="preorder">PreOrder</h2>
<p>Put parent in result, add right child to stack and go to left child.<br>
If no left child, go to nearest right child i.e <strong>stack.top()</strong></p>
<pre class=" language-cpp"><code class="prism  language-cpp"><span class="token keyword">while</span> <span class="token punctuation">(</span>root <span class="token operator">||</span> <span class="token operator">!</span>stk<span class="token punctuation">.</span><span class="token function">empty</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>root<span class="token punctuation">)</span>
    <span class="token punctuation">{</span>
	    preorder<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span>root<span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token keyword">if</span> <span class="token punctuation">(</span>right<span class="token punctuation">)</span> stk<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span>right<span class="token punctuation">)</span><span class="token punctuation">;</span>
		root <span class="token operator">=</span> root <span class="token operator">-</span><span class="token operator">&gt;</span> left<span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    <span class="token keyword">else</span>
    <span class="token punctuation">{</span>
        root <span class="token operator">=</span> stk<span class="token punctuation">.</span><span class="token function">top</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        stk<span class="token punctuation">.</span><span class="token function">pop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="inorder">InOrder</h2>
<p>Add parent to stack and go to left child.<br>
If no left child, go back to parent, put it in result and go to right child.</p>
<pre class=" language-cpp"><code class="prism  language-cpp"><span class="token keyword">while</span> <span class="token punctuation">(</span>root <span class="token operator">||</span> <span class="token operator">!</span>stk<span class="token punctuation">.</span><span class="token function">empty</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>root<span class="token punctuation">)</span>
    <span class="token punctuation">{</span>
		stk<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span>root<span class="token punctuation">)</span><span class="token punctuation">;</span>
		root <span class="token operator">=</span> root <span class="token operator">-</span><span class="token operator">&gt;</span> left<span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    <span class="token keyword">else</span>
    <span class="token punctuation">{</span>
        root <span class="token operator">=</span> stk<span class="token punctuation">.</span><span class="token function">top</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        inorder<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span>root<span class="token punctuation">)</span><span class="token punctuation">;</span>
        root <span class="token operator">=</span> root <span class="token operator">-</span><span class="token operator">&gt;</span> right
        stk<span class="token punctuation">.</span><span class="token function">pop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="postorder">PostOrder</h2>
<h1 id="morris-traversal">Morris Traversal</h1>

