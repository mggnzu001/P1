- What are the two main differences between dynamic programming and divide-and-conquer? #card
  - **Similarities**: Both solve problems by dividing into subproblems
  - **Key Difference**: In divide-and-conquer, subproblems don't overlap (solutions not reused). In dynamic programming, subproblems overlap (solutions stored for reuse)

- What is the coin-row problem and what technique solves it efficiently? #card
  - **Problem**: Given a row of coins with values, select non-adjacent coins to maximize total value
  - **Solution**: Dynamic programming
  - **Recurrence**: F(n) = max{F(n-1), c_n + F(n-2)}
  - **Example**: For coins [5,1,2,10,6], optimal value is 15 (coins at positions 1 and 4)

- What is the time efficiency of the brute-force coin-row algorithm? #card
  - **Efficiency**: Exponential - Θ(φ^n) where φ = (1+√5)/2 (golden ratio)
  - **Reason**: Similar to recursive Fibonacci computation, creates exponential tree of recursive calls
  - **Better approach**: Dynamic programming in Θ(n) time

- Describe the change-making problem and its dynamic programming solution #card
  - **Problem**: Given denominations d₁,...,dₘ and amount n, find minimum coins needed
  - **Recurrence**: F(n) = min{F(n-dⱼ)} + 1 for all denominations dⱼ ≤ n
  - **Base case**: F(0) = 0
  - **Efficiency**: Θ(nm) time, Θ(n) space

- What is the coin-collecting problem on a board? #card
  - **Problem**: Robot collects coins on n×m board, moving only right or down from top-left to bottom-right
  - **Goal**: Maximize coins collected
  - **Recurrence**: F(i,j) = max{F(i-1,j), F(i,j-1)} + C[i,j]
  - **Efficiency**: Θ(nm) time and space

- What is the 0-1 knapsack problem? #card
  - **Given**: n items with weights w₁,...,wₙ and values v₁,...,vₙ, knapsack capacity W
  - **Goal**: Select items (at most one of each) to maximize total value without exceeding capacity
  - **Recurrence**: F(i,j) = max{F(i-1,j), vᵢ + F(i-1,j-wᵢ)}
  - **Efficiency**: Θ(nW) time, Θ(nW) or Θ(W) space

- What is the memory function method? #card
  - **Approach**: Top-down dynamic programming with memoization
  - **How it works**: Uses recursion but stores computed values in table to avoid recomputation
  - **Advantage**: Only computes needed subproblems (unlike bottom-up which computes all)
  - **Trade-off**: Has recursion overhead

- What is the optimal binary search tree problem? #card
  - **Given**: Keys a₁<...<aₙ with search probabilities p₁,...,pₙ
  - **Goal**: Construct BST minimizing average number of comparisons
  - **Recurrence**: C[i,j] = min{C[i,k-1] + C[k+1,j]} + Σpᵢ for i≤k≤j
  - **Efficiency**: Θ(n³) time, Θ(n²) space

- What does Warshall's algorithm compute? #card
  - **Purpose**: Finds transitive closure of a directed graph
  - **Transitive closure**: R⁺[i,j] = 1 if there's a path from vertex i to vertex j
  - **Recurrence**: R⁽ᵏ⁾[i,j] = R⁽ᵏ⁻¹⁾[i,j] ∨ (R⁽ᵏ⁻¹⁾[i,k] ∧ R⁽ᵏ⁻¹⁾[k,j])
  - **Efficiency**: Θ(n³) time, Θ(n²) space (can be done in-place)

- What does Floyd's algorithm compute? #card
  - **Purpose**: Finds all-pairs shortest paths in weighted graph
  - **Recurrence**: D⁽ᵏ⁾[i,j] = min{D⁽ᵏ⁻¹⁾[i,j], D⁽ᵏ⁻¹⁾[i,k] + D⁽ᵏ⁻¹⁾[k,j]}
  - **Base case**: D⁽⁰⁾ is the weight matrix
  - **Efficiency**: Θ(n³) time, can be done in-place
  - **Limitation**: Doesn't work with negative-weight cycles

- What is Huffman coding used for? #card
  - **Purpose**: Data compression using variable-length prefix-free codes
  - **Key idea**: Assign shorter codes to more frequent characters
  - **Algorithm**: Greedy - repeatedly combine two least-frequent nodes
  - **Property**: Produces optimal prefix-free code
  - **Efficiency**: O(n log n) with priority queue

- How do you construct a Huffman tree? #card
  - **Steps**:
    1. Create leaf node for each character with its frequency
    2. Build min-heap of all nodes
    3. While heap has >1 element:
       - Extract two minimum-frequency nodes
       - Create internal node with sum of frequencies
       - Make extracted nodes children, insert back into heap
  - **Result**: Optimal binary tree for encoding

- What is the principle behind greedy algorithms in dynamic programming? #card
  - **Greedy vs DP**: 
    - Greedy makes locally optimal choice at each step
    - DP considers all possibilities and stores results
  - **When greedy works**: Problem has optimal substructure + greedy choice property
  - **Examples**: Huffman coding, some graph problems
  - **Risk**: Greedy doesn't always give optimal solution (e.g., general knapsack)

  - What is the rod-cutting problem? #card
  - **Problem**: Given rod of length n and prices p₁,...,pₙ for pieces of different lengths, find maximum revenue
  - **Recurrence**: R(n) = max{pᵢ + R(n-i)} for 1≤i≤n
  - **Base case**: R(0) = 0
  - **Efficiency**: Θ(n²) time with dynamic programming
  - **Similar to**: Change-making problem

- What is the matrix chain multiplication problem? #card
  - **Problem**: Find optimal order to multiply n matrices to minimize total scalar multiplications
  - **Given**: Matrix dimensions p₀×p₁, p₁×p₂,...,pₙ₋₁×pₙ
  - **Recurrence**: M[i,j] = min{M[i,k] + M[k+1,j] + pᵢ₋₁·pₖ·pⱼ} for i≤k<j
  - **Efficiency**: Θ(n³) time
  - **Number of ways**: Catalan number Cₙ₋₁ ∈ Θ(4ⁿ/n^(3/2))

- What are Catalan numbers and where do they appear? #card
  - **Formula**: C(n) = (2n choose n)/(n+1) = (2n)!/((n+1)!·n!)
  - **Recurrence**: C(n) = Σ C(k)·C(n-1-k) for k=0 to n-1, C(0)=1
  - **Growth**: Θ(4ⁿ/n^(3/2))
  - **Applications**: Binary trees with n nodes, ways to parenthesize n+1 factors, polygon triangulations

- What is the longest common subsequence (LCS) problem? #card
  - **Problem**: Find longest subsequence common to two sequences (not necessarily contiguous)
  - **Example**: LCS of "ABCDGH" and "AEDFHR" is "ADH" (length 3)
  - **Recurrence**: 
    - If xₘ = yₙ: L[i,j] = L[i-1,j-1] + 1
    - Else: L[i,j] = max{L[i-1,j], L[i,j-1]}
  - **Efficiency**: Θ(mn) time
  - **Application**: DNA sequence comparison, file diff utilities

- What is the difference between a subsequence and a substring? #card
  - **Substring**: Contiguous sequence of characters (e.g., "BCD" in "ABCDE")
  - **Subsequence**: Characters in same order but not necessarily contiguous (e.g., "ACE" in "ABCDE")
  - **Property**: Every substring is a subsequence, but not vice versa
  - **In LCS**: We find longest common subsequence (more general problem)

- What is string edit distance (Levenshtein distance)? #card
  - **Problem**: Minimum operations (insert/delete/replace) to transform one string to another
  - **Recurrence**: 
    - If chars match: D[i,j] = D[i-1,j-1]
    - Else: D[i,j] = 1 + min{D[i-1,j], D[i,j-1], D[i-1,j-1]}
  - **Efficiency**: Θ(mn) time and space
  - **Applications**: Spell checking, DNA analysis, plagiarism detection

- What is the traveling salesman problem (TSP)? #card
  - **Problem**: Find shortest tour visiting all n cities exactly once and returning to start
  - **Complexity**: NP-hard
  - **Brute force**: (n-1)!/2 tours to check
  - **Dynamic programming**: Held-Karp algorithm in Θ(n²·2ⁿ) time
  - **Recurrence**: C(S,i) = min{C(S-{i}, j) + d[j,i]} for j∈S-{i}

- What is the subset sum problem? #card
  - **Problem**: Given set of integers and target sum, determine if subset exists that sums to target
  - **Variant of**: Knapsack problem (weights = values)
  - **Recurrence**: T[i,s] = T[i-1,s] ∨ T[i-1, s-aᵢ]
  - **Efficiency**: Θ(n·S) pseudo-polynomial time
  - **Complexity**: NP-complete

- What does pseudo-polynomial time mean? #card
  - **Definition**: Time complexity polynomial in numeric value of input, not input size
  - **Example**: Θ(n·W) for knapsack where W is capacity value
  - **Issue**: W could be exponential in number of bits to represent it
  - **Contrast**: True polynomial is based on input size (number of bits)
  - **Implication**: Not considered efficient for large numeric values

- What is the principle of optimality in dynamic programming? #card
  - **Definition**: An optimal solution contains optimal solutions to subproblems
  - **Requirement**: Problem must have optimal substructure property
  - **Example**: In shortest path, if A→B→C is optimal, then B→C must be optimal
  - **Counter-example**: Longest simple path doesn't have this property
  - **Importance**: Necessary for DP to work correctly

- What is memoization? #card
  - **Definition**: Storing results of expensive function calls and returning cached result when same inputs occur
  - **In DP**: Top-down approach that combines recursion with caching
  - **Advantages**: Only computes needed subproblems, intuitive recursive structure
  - **Disadvantages**: Recursion overhead, may use more space
  - **Implementation**: Use hash table or array to store computed values

- When should you use bottom-up vs top-down DP? #card
  - **Bottom-up (tabulation)**:
    - When all subproblems must be solved anyway
    - Better space efficiency possible
    - No recursion overhead
  - **Top-down (memoization)**:
    - When only some subproblems needed
    - More intuitive to formulate
    - Natural recursion structure
  - **Same time complexity**: Both typically Θ(n²) or similar

- What is the space optimization technique in DP? #card
  - **Observation**: Often only need previous row/column, not entire table
  - **Technique**: Use 1D array instead of 2D table
  - **Example**: In knapsack, only need F[i-1,*] to compute F[i,*]
  - **Space reduction**: From Θ(nW) to Θ(W)
  - **Trade-off**: Can't reconstruct full solution without storing more info

- How do you reconstruct the actual solution in DP (not just optimal value)? #card
  - **Method 1**: Store parent/previous pointers while computing
  - **Method 2**: Retrace decisions by comparing values in completed table
  - **Example (knapsack)**: If F[i,j] ≠ F[i-1,j], item i was included
  - **Time**: Usually O(n) to reconstruct after O(n²) or O(n³) computation
  - **Space**: May need additional array to store decisions

- What is the World Series odds problem? #card
  - **Problem**: Team A needs i wins, team B needs j wins. Find probability A wins series.
  - **Recurrence**: P(i,j) = p·P(i-1,j) + (1-p)·P(i,j-1)
  - **Base cases**: P(0,j) = 1 for j>0, P(i,0) = 0 for i>0
  - **Table size**: (n+1) × (n+1) where n is games needed to win
  - **Efficiency**: Θ(n²) time and space

- What is the minimum edit distance problem with custom costs? #card
  - **Extension**: Different costs for insert, delete, replace operations
  - **Recurrence**: 
    - D[i,j] = min{
      D[i-1,j] + delete_cost,
      D[i,j-1] + insert_cost,
      D[i-1,j-1] + replace_cost (if chars differ)
    }
  - **Application**: More accurate modeling (e.g., keyboard distance for typos)
  - **Efficiency**: Still Θ(mn)

- What is the partition problem? #card
  - **Problem**: Partition set of integers into two subsets with equal sum
  - **Prerequisite**: Total sum must be even
  - **Reduction to**: Subset sum with target = total_sum/2
  - **Recurrence**: P[i,s] = P[i-1,s] ∨ P[i-1,s-aᵢ]
  - **Complexity**: NP-complete, but pseudo-polynomial DP exists

- What is the technique of reducing one problem to another in DP? #card
  - **Concept**: Transform problem A into problem B with known solution
  - **Example**: Partition problem → Subset sum problem
  - **Benefits**: Reuse existing algorithms, prove complexity relationships
  - **Process**: 
    1. Preprocess input for problem A
    2. Apply algorithm for problem B
    3. Post-process output if needed
  - **Complexity**: Must account for transformation time

- What is the palindrome partitioning problem? #card
  - **Problem**: Partition string into minimum number of palindromic substrings
  - **Approach**: 
    1. Precompute which substrings are palindromes: Θ(n²)
    2. Use DP: C[i] = min{C[j-1] + 1} where s[j..i] is palindrome
  - **Efficiency**: Θ(n²) time and space
  - **Example**: "ababbbabbababa" → ["abab", "bbabb", "ababa"] (3 pieces)

- What is the egg dropping problem? #card
  - **Problem**: With k eggs and n-floor building, find minimum worst-case drops to determine critical floor
  - **Recurrence**: F(k,n) = 1 + min{max{F(k-1,x-1), F(k,n-x)}} for 1≤x≤n
  - **Interpretation**: Drop from floor x: if breaks check below (k-1 eggs), else check above
  - **Efficiency**: Θ(kn²) with naive DP
  - **Optimization**: Can improve to Θ(kn log n)

- What is the box stacking problem? #card
  - **Problem**: Stack boxes to maximize height, where each box must be strictly smaller than one below
  - **Approach**: 
    1. Generate all rotations of boxes (3n boxes)
    2. Sort by base area (decreasing)
    3. DP: H[i] = max{H[j] + h[i]} where box j can be under box i
  - **Efficiency**: Θ(n²) after sorting
  - **Similar to**: Longest increasing subsequence

- What is the difference between overlapping subproblems and optimal substructure? #card
  - **Overlapping subproblems**: Same subproblems solved multiple times (enables memoization)
  - **Optimal substructure**: Optimal solution contains optimal solutions to subproblems (enables DP correctness)
  - **Both needed**: DP requires both properties
  - **Examples**: 
    - Fibonacci has both
    - Shortest path has both
    - Longest simple path has optimal substructure but overlapping could be limited

- What is the coin change problem (counting ways)? #card
  - **Problem**: Count number of ways to make change for amount n with given denominations
  - **Recurrence**: C(i,n) = C(i-1,n) + C(i,n-dᵢ)
  - **Interpretation**: Ways without using coin i + ways using at least one coin i
  - **Base cases**: C(i,0) = 1, C(0,n) = 0 for n>0
  - **Efficiency**: Θ(nm) time
  - **Different from**: Minimum coins problem (finds min count, not ways)

- How does Warshall's algorithm avoid recomputation? #card
  - **Key insight**: Can overwrite matrix in-place
  - **Why it works**: R⁽ᵏ⁾[k,*] = R⁽ᵏ⁻¹⁾[k,*] and R⁽ᵏ⁾[*,k] = R⁽ᵏ⁻¹⁾[*,k]
  - **Explanation**: Row k and column k don't change when processing vertex k
  - **Space optimization**: Θ(n²) instead of Θ(n³)
  - **Implementation**: Single n×n matrix updated in place

- How can you detect negative cycles using Floyd's algorithm? #card
  - **Method**: After running algorithm, check diagonal of distance matrix
  - **Indicator**: If D[i,i] < 0 for any i, negative cycle exists
  - **Reason**: Negative diagonal means shorter path from vertex to itself
  - **Limitation**: Can't compute shortest paths when negative cycles exist
  - **Alternative**: Use Bellman-Ford algorithm which explicitly detects negative cycles

- What is the bitwise optimization for Warshall's algorithm? #card
  - **Technique**: Represent each row as bit string, use bitwise OR
  - **Operation**: If R[i,k]=1, then Row[i] = Row[i] OR Row[k]
  - **Advantage**: Process entire row in parallel with single bitwise operation
  - **Implementation**: Requires bit manipulation support in language
  - **Speedup**: Can be significantly faster on modern hardware

- What is the time complexity analysis technique for nested loops in DP? #card
  - **Standard approach**: Count total iterations of innermost operation
  - **For triple nested**: C(n³) = Σᵢ Σⱼ Σₖ 1 = n³
  - **With dependencies**: Must account for loop bounds depending on outer variables
  - **Example**: Σᵢ₌₁ⁿ Σⱼ₌ᵢⁿ (j-i+1) = Θ(n³) for optimal BST
  - **Technique**: Use summation formulas or geometric series

- When does greedy algorithm work instead of full DP? #card
  - **Requirements**:
    1. Optimal substructure (like DP)
    2. Greedy choice property (local optimum leads to global)
  - **Examples that work**: Huffman coding, MST, Dijkstra's shortest path
  - **Examples that don't**: 0-1 knapsack, longest path in general graph
  - **Advantage**: Usually faster - O(n log n) vs O(n²)
  - **Challenge**: Proving greedy choice property is often difficult

- What is the technique for proving DP correctness? #card
  - **Method**: Mathematical induction on subproblem size
  - **Steps**:
    1. Prove base cases are correct
    2. Assume optimal solution for smaller subproblems
    3. Prove recurrence produces optimal solution for larger problem
    4. Show all cases are covered
  - **Alternative**: Prove by contradiction (exchange argument)
  - **Common mistake**: Forgetting to prove optimal substructure exists

- What is the pattern for most DP recurrences? #card
  - **Structure**: F(n) = optimize{F(smaller problems) + cost of merging}
  - **Optimize**: Usually min or max
  - **Smaller problems**: Size n-1, n/2, or based on decision variable
  - **Cost**: Often constant or dependent on subproblem sizes
  - **Examples**:
    - Fibonacci: F(n) = F(n-1) + F(n-2) [sum]
    - Knapsack: F(i,w) = max{F(i-1,w), vᵢ+F(i-1,w-wᵢ)} [max + value]
