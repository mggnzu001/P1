# Exam Questions Flashcards - Theory of Computation & Algorithms

## Direct Questions from Exams

### Question 8 - Turing Machine Design #card
Design a Turing Machine that accepts an unequal number of 0s and 1s. Thus, it should accept strings like 00111 and 10110, but reject strings like 0011 and 1010. You may choose to do that with any type of Turing Machine that has been covered in the module.

Provide the full definition of the TM. The transition function may be drawn (using consistent common notation), listed in a list of functions (adhering to the definition of the function), or shown in a table with the states (first column the states, first row the alphabet).

**ANSWER:**
This is fairly similar to exercise 8.2.2 and 8.4.6, but then the other way around (uneven rather than even). The multi-tape is the easiest, and instead of making it go to the final state upon the # (or whatever the marker is on the scratch tape), it should go to the final state if it the cell with # is *not* under the tape head, i.e., if the cell on the scratch tape has a blank.

M = ({q0,q1,q2},{0,1},{0,1,B},q0,q2)

---

### Question 9 - Language Reduction #card
L1 reduces to L2. We know that L2 is a recursive language. What can be said about L1? Prove it.

**ANSWER:**
L1 is also recursive.

**Proof:**
L2 is recursive, so has an algorithm for it, which returns y/n for sure.
Since it does reduce (given in statement), there must be an algorithm A_R for that reduction converting w in to 'R(w)' (A2's input).
Then we can construct an algorithm A1 such that M1's input is converted to one for M2 for A2, and we can use A2's output for A1's output. So then w in L1 equiv R(w) in L2.

---

### Question 10 - Algorithm Analysis #card
Consider the following algorithm:
```
ALGORITHM what(int [] A, int i, int j)
if i == j then
    return A[i]
if i == j-1 then
    if A[i] < A[j] then
        return A[i]
    else
        return A[j]
k = (i+j) / 2
m1 = what(A, i, k)
m2 = what(A, k+1, j)
if m1 < m2 then
    return m1
else
    return m2
```

i) What does the algorithm above do? What strategy (algorithmic pattern) does this algorithm use?
ii) Determine the performance of this algorithm by setting up a recurrence relation for the basic operations being performed and solving it using the Master Theorem. Show all your work.

**ANSWER:**
i) It uses recursion to find the minimum value in an array. It employs a divide and conquer strategy.

ii) Basic operation is comparison. In the worst case 3 comparisons are done on each step and 2 recursive calls, each of which operates on half the array, thus:
C(n) = 2 C(n/2) + 3

In terms of the Master Theorem a = 2, b = 2, d = 0.
This fits the a > b^d case so efficiency is Θ(n^(log_b a)) = Θ(n^(log_2 2)) = Θ(n).

---

### Question 11 - Warshall's Algorithm #card
Given the following adjacency matrix:
```
[1 1 0]
[0 0 1]
[0 1 0]
```

i) Show the steps in the execution of Warshall's algorithm for transitive closure applied to this matrix.
ii) From the outcome, list a pair of nodes (a, b) where node b is not reachable from node a. Note that a and b should be numbers in the range 1, …, 3.

**Solution:**
i)
R^1 = [1 1 0]
      [0 0 1]
      [0 1 0] (no change)

R^2 = [1 1 1]
      [0 0 1]
      [0 1 1]

R^3 = [1 1 1]
      [0 1 1]
      [0 1 1]

ii) either (2, 1) or (3, 1).

---

### Question 2a - Big-O Analysis #card
Explain your answers in each case below:
i. Is O(2^n) ⊆ O(n!)? 
ii. Is O(log_2 n) ⊆ O(1)?
iii. Is Θ(n) ⊆ Θ(n!)?

**Answer:**
i) Yes. n! grows faster than 2^n but Big Oh provides an upper bound

ii) No. log_2 n grows faster than a constant

iii) No. n! grows faster than n so they are in different efficiency classes. And the class is a subset of itself.

---

### Question 2b - Strassen's Algorithm #card
Consider the pseudocode for Strassen's algorithm for matrix multiplication:

Set up a recurrence relation for the number of basic operations being performed by this algorithm and solve it using the Master Theorem.

**Answer:** 
T(n) = 7T(n/2) + Θ(n^2). 
a=7, b=2, d=2. 
So 7>2^2. 
So T(n) is in Θ(n^(log_2 7)) = Θ(n^2.807).

---

### Question 2c - Floyd's Algorithm #card
Give pseudocode for Floyd's algorithm to find the shortest path between all vertices, given a weighted connected graph.

**Answer:**
```
floyd(W[1..n,1..n])
for k=1 to n
    for i=1 to n
        for j=1 to n
            W[i,j] = min(W[i,j], W[i,k]+W[k,j])
```

---

### Question 2d - Graph Representation #card
Explain how a weighted connected graph needs to be represented for Floyd's algorithm to work.

**Answer:**
Adjacency matrix where infinity represents no edge between two vertices, other values represent distance between vertices (so 0 between vertex x and itself).

---

### Question 3a - NFA Conversion #card
Can every NFA N be converted to an NFA N' with a single accept state that accepts the same language as N? If so, explain how to do so. If not, given an example.

**Answer:**
Yes it can. Informally, add a new state p, add an epsilon transition from every accept state of N to p, and make p the only accept state.

---

### Question 3b - Context-Free Grammar #card
Construct a context-free grammar that generates the following language:
L = {w | w ∈ {a,b,c}* and w = w^r}. So every word in L is a palindrome made up of the letters a, b, and c.

**Answer:**
S → X
X → aXa | bXb | cXc
X → a | b | c
X → ε

---

### Question 3c - CFG Closure Property #card
Prove that the context-free languages are closed under the * operation.

**Answer:**
Let G1 be a CFG that describes the language L1. Give each of the variables in G1 the subscript 1. Let S_1 be the start symbol for G1.

We construct a new CFG G from G1 that accept L1*.
Let S be a new variable (not occurring in G1). S is the start symbol for G.
Add the following rules: S → ε | SS_1.

---

### Question 4a - Algorithm Techniques #card
Brute force and divide-/decrease-and-conquer are techniques most commonly used for problem solving. Name and briefly describe any two other techniques.

**Answer:**
Space-time: use additional data structures/memory/variables/space in order to make a faster solution/algorithm possible.

Dynamic programming: solve overlapping subproblems by storing intermediate results in an array where they are later accessed instead of being recomputed

Transform and conquer: solve a problem more easily by changing it to a more convenient instance of the same problem, or using a different representation, or transforming it to another problem whose solution can be transformed into an answer to the original

Greedy: solve a problem by making the optimal choice at each step

---

### Question 4b - Master Theorem Interpretation #card
Consider the Master Theorem: If T(n) = aT(n/b) + f(n) then
- T(n) is O(n^d) if a < b^d
- T(n) is O(n^d log n) if a = b^d
- T(n) is O(n^(log_b a)) if a > b^d

i. Which letter indicates how much recursion an algorithm does: a, b or d?
ii. Which indicates how many operations each recursive call does: a, b or d?
iii. What does the remaining letter indicate?

**Answer:**
i. a
ii. d
iii. what fraction of the input is the argument to each recursive call (b)

---

### Question 4c - Boyer-Moore and Horspool #card
Show the shift table that would be used by the Boyer-Moore and Horspool algorithms when searching for the string DESEEDED in a text; and state by how many positions each algorithm would shift the pattern (DESEEDED) after their very first attempt i.e. when they fail to find that string at the start of the text "HE-FOUND-AND-DESEEDED-IT" (state clearly which answer is BM and which Horspool).

**Answer:**
Array: D = 2; E = 1; S = 5. 
Horspool moves 2; BM moves 7.

---

### Question 5a - NFA Complement #card
Let N be an NFA, and let N' be an NFA obtained from it by letting the accept states of N' be the reject states of N, and the reject states of N' the accept states of N (so N' is obtained from N by swapping around the accept and reject states). Is the language accepted by N' the complement of the language accepted by N? If it is, explain why it is. If it is not, give an example to show that it isn't.

**Answer:**
No it's not. Many examples. Consider the following NFA N over {0,1}. It accepts the language {0}. N' accepts the language {}, which is not the complement of L(N). The problem cases are those where the NFA gets stuck.

---

### Question 5b - Regular Expression #card
Give a regular expression that accepts the following language:
L = { w | w has an odd number of 1s, and ends with a 0}.

**Answer:**
One of many options: 0*10*(0*10*10*)*0

---

### Question 5c - Pumping Lemma #card
Complete the following proof to prove that the following language is not regular:
L = { a^n b^n a^n | n≥0}.

Proof: Assume L is regular and consider the word w = …… where p is the pumping length. By the pumping lemma, w must be a word of the form xyz where the length of xy is no greater than p and y has a length greater than 0. This means that the word xy^2z is not a word in L because…….: a contradiction.

**Answer:**
Assume L is regular and consider the word w = a^p b^p a^p where p is the pumping length. By the pumping lemma, w must be a word of the form xyz where the length of xy is no greater than p, and y has a length greater than 0. This means that the word xy^2z is not a word in L because it has the form a^q b^p a^p where q>p (since xy consists of 0s only): a contradiction.

---

### Question 2 - Efficiency Classes #card
Which TWO of the following statements are TRUE?
i. Θ(n + log n) = Θ(n)
ii. if x ∈ O(n log n) then x ∈ Θ(n log n)
iii. if x ∈ O(n log n) then x ∈ O(n^2)
iv. if x ∈ O(n log n) then x ∈ O(n)

**Answer:**
i. Θ(n + log n) = Θ(n)
iii. if x∈ O(n log n) then x∈ O(n^2)

---

### Question 2b - Exponentiation Techniques #card
Show the different approaches of the algorithmic techniques below, using the example of exponentiation (a^N). Each answer should take one line.
i. Brute force
ii. Divide and conquer
iii. Decrease and conquer
iv. Transform and conquer

**Answer:**
i. a * a * a …. * a N times
ii. (a^(N/2)) * (a^(N/2))
iii. (a^(N-1)) * a OR (a^(N/2))^2
iv. Horner's rule OR Binary Exponentiation

---

### Question 2c - Greedy and Space-Time #card
Two other techniques are Greedy Algorithms and Space-Time-Trade-off. Briefly describe these 2 approaches to problem solving (1 line each).

**Answer:**
Space-time: use additional data structures/memory/variables/space in order to make a faster solution/algorithm possible

Greedy: make the optimum choice at each step.

---

### Question 2e - Horspool's Algorithm #card
You are searching for the first occurrence of the string REFERER in a text.
i. Show the shift table that Horspool's algorithm would use.
ii. Show the good-suffix shift table that the Boyer-Moore algorithm would use for this search string REFERER.

**Answer:**
i. E=1, F=4, R=2

ii. 
Index: 1, 2, 3, 4, 5, 6
Values: 6, 2, 6, 6, 6, 6

---

### Question 2f - Dynamic Programming Problem #card
You are given a row of integers. You can choose as many as you like except that you cannot take any 2 integers that are adjacent (next to each other). For example, if the row has values 4, 2, 8, 6 then you can take the 4 only of you don't take the 2, you can take the 2 only if you take neither the 8 nor the 4, … you can take the 6 only if you don't take the 8.

i. State in words or pseudocode how you would you use Dynamic Programming to find the maximum value you can take
ii. Show what the array would contain after solving the example below: 4, 2, 8, 6 (Maximum is 12 - take the 4 and the 8).

**Answer:**
i. Go from start to end of list, each time choosing max(with new value, without new value) and storing it in the array
For the j'th item, A[j] is set to max(A[j-2]+newval, A[j-1])

ii. Array: [4, 4, 12, 12]

---

### Question 3a - DFA to NFA Conversion #card
Prove, using the formal definitions of Deterministic Finite Automata and Non-Deterministic Finite Automata, that for every Deterministic Finite Automaton there is a Non-Deterministic Finite Automaton that accepts exactly the same language.

**Answer:**
Let D = (Q, Sigma, delta, q0, F). We need to find an NFA N such that N accepts the same language as D.

We define N as: (Q,Sigma,delta', q0, F) where delta' is defined as follows:

For every q in Q and every s in Sigma, delta'(q,s) = {delta(q,s)}
For every q in Q, delta'(q,epsilon) = emptyset

---

### Question 3b - Regular Language Closure #card
Suppose we want to prove that for any regular language A, A* is also regular. We know that if A is regular, then there is a Non-Deterministic Finite Automaton N such that N accepts A. Now, from N we construct a new Non-Deterministic Automaton N' as follows: for every accept state s of N, add an epsilon-transition from s to the start state of N (if there isn't one already). Does N' accept A*? If it does, explain why in detail. If it does not, explain why not, indicate what language it accepts, and explain how to modify N' so that it accepts A*.

**Answer:**
N' does not always accept A*.

If A contains the empty string, then N' accepts A*. If not, then N' accepts every element of A* except the empty string.

To ensure that N' always accepts A*:
- add a new start state, say q, to N';
- make q an accept state;
- add an epsilon-transition from q to the old start state of N'.

---

### Question 1a - Technique Explanations #card
Briefly explain the techniques below. Be sure the difference between the two problem-solving strategies in each pair is clear.
1. divide-and-conquer and decrease-and-conquer
2. space-and-time tradeoff and problem reduction
3. dynamic programming ("DP") and DP with memory functions

**Answer:**
div-conq: solve problem by combining solutions of smaller subproblems
decrease-conq: solve problem by solving smaller instance of that same problem

space-time: solve problem faster by using more space (or vice versa, if space is the problem)
prob reduction: solve problem A by transforming it to an instance of another problem B

DP: solve problem by combining solutions of overlapping smaller subproblems
DP with mem func: as above, but proceed top down instead of bottom up

---

### Question 1b - True/False Statements #card
State whether each of the following is true or false:
1. Θ(n + log n) = Θ(n)
2. O(n log n) = O(n)
3. if p ∈ O(n log n) then p ∈ O(n^2)
4. if p ∈ Θ(n log n) then p ∈ Θ(n^2)
5. if p ∈ Ω(n log n) then p ∈ Ω(n)

**Answer:**
1. T 
2. F 
3. T 
4. F 
5. T

---

### Question 1d - Master Theorem Application #card
Use the Master Theorem to find the complexity of waat below, showing your working.
```
waat(x) { 
    if x < 3 return 'a' 
    else return waat(2x/3) ++ waat(2x/3) 
} // ++ is concatenate
```

**Answer:**
a is 2, b is 3/2, d is 0
so a > b^d 
so Θ(n^(log_(3/2) 2))

---

### Question 2a - Horspool Algorithm Table #card
Consider searching for the first occurrence of the octal pattern 061606 in octal text 02040606061606
1. Show the shift table that would be used if Horspool's algorithm is applied.

**Answer:**
Horspool shift table:
0=1, 1=3, 6=2, others=6

---

### Question 2a - Boyer-Moore Good Suffix #card
Show the good-suffix table that Boyer-Moore would use for searching pattern 061606.

**Answer:**
Good-suffix table:
Index: 1, 2, 3, 4, 5
Values: 2, 4, 4, 4, 4

---

### Question 1 - Euclid's GCD #card
What does the following algorithm do?
```
ALGORITHM mystery(int x,int y)
while y ≠ 0 do
    t ← x mod y
    x ← y
    y ← t
return x
```

**Answer:** 
It computes the gcd of x and y.

---

### Question 1b - Big-O Analysis Questions #card
Explain your answers in each case below:
i) Is O(n!) ⊆ O(2^n)?
ii) Is O(n log_2 n) ⊆ O(n!)?
iii) Is Θ(n^3) ⊆ Θ(n^2)?

**Answer:**
i) No. n! grows faster than 2^n.

ii) Yes. n log_2 n grows slower than n! but big Oh provides an upper bound.

iii) No. n^3 grows faster than n^2 so an n^3 function is not in Θ(n^2). So there are elements of Θ(n^3) that are not in Θ(n^2).

---

### Question 1c - Towers of Hanoi #card
Consider the following algorithm:
```
ALGORITHM whoknows(int x,int y, int z, int a)
if a > 0 do
    whoknows(x,z,y,a-1)
    print x, z, a
    whoknows(y,x,z,a-1)
```

i) What does the algorithm above do?
ii) Set up a recurrence relation for the number of basic operations being performed and solve it. Show all your work.

**Answer:**
i) It solves the Towers of Hanoi problem.

ii) T(0) = 0. T(n) = T(n-1) + 1 + T(n-1) = 2T(n-1) + 1 = 2(2T(n-2) + 1) + 1 =… 2^k T(n-k) + (2^k-1). Set k=n. Then T(n) = 2^n T(0) + 2^n-1 = 2^n-1

---

### Question 1d - Algorithm Efficiency Classes #card
Consider the two algorithms below. Are they in the same efficiency class or not? Justify your answer.
```
ALGORITHM A2(int n > 0)
if n=1 return 1 else return 1 + A2(n/2)

ALGORITHM A5(int n > 0)
if n=1 return 1 else return 1 + A5(n/5)
```

**Answer:**
Yes they are. A2 performs roughly log_2 n basic operations and A5 performs roughly log_5 n basic operations. Logarithmic functions grow at the same rate, regardless of the base.

---

### Question 1 - Turing Machine Computation #card
Consider the following Turing Machine for some language or decision problem that accepts by final state.

a) Show the computation of the input string 011, using the notation of instantaneous descriptions.
b) Describe the situation that the Turing Machine is in when it is at that last instantaneous description.

**Answer:**
a) q_0 011 ⊢ Xq_1 11 ⊢ q_2 XY1 ⊢ Xq_0 Y1 ⊢ XYq_3 1 (and then no more moves are possible)

b) the TM halts in a non-final state and so rejects the input (alternative terminology: it dies/stops, and that it will answer 'no' to the question whether the input string is in the language that the TM is designed for)

---

### Question 3 - Recursive vs RE Languages #card
Sketch or describe the differences between recursive, recursively enumerable, and non-recursively enumerable languages in the context of Turing machines, and how they relate to something like the Hello World Problem specifically and to algorithms and procedures more generally.

**Answer:**
The recursive ones correspond to the algorithms, always a y or n on any given input. The RE ones [that are not recursive] correspond to the procedures that can give a y but that's it, and non-RE gets into knots (like the HWP or Foo problem) and no TM can do anything with it.

---

### Question 4a - Theta Analysis #card
Answer True or False to each assertion below and explain your answers in each case:
i) Θ(n log_2 n) ⊆ Θ(n)
ii) if y ∈ O(1) then y ∈ O(n)
iii) if x ∈ Ω(n!) then x ∈ Ω(n^2)

**Answer:**
i) False. Big-theta is an exact bound so it is not possible for an algorithm to be in two different theta efficiency classes.

ii) True. Big-O is an upper bound so that if an algorithm is in a better efficiency class (e.g., constant) it is also bound above by a worse efficiency class (e.g., linear).

iii) True. Big-Omega is a lower bound so that if an algorithm is in a worse efficiency class (e.g., factorial) it is also bound below by a better efficiency class (e.g., quadratic).

---

### Question 4c - Binary Search Analysis #card
Consider the following algorithm assuming A is a sorted array. What strategy does it use and what is its worst-case complexity?
```
ALGORITHM strange(int [] A, int i, int j, int x)
if i >= j do
    k = i + (j - i)/2
    if A[k] == x do
        return TRUE
    if A[k] > x do
        return strange(A, i, k-1, x)
    else
        return strange(A, k+1, j, x)
else
    return FALSE
```

i) What does the algorithm above do? What strategy does it use?
ii) Set up a recurrence relation and solve using Master Theorem.

**Answer:**
i) It uses a binary search to determine if x is in the array A and returns TRUE if it is or FALSE otherwise. This is an example of a decrease and conquer algorithm.

ii) Basic operation is comparison. In the worst case x is not found in the list. Two comparisons are done and the size of the array is halved on each recursive step, thus:
C(n) = C(n/2) + 2

In terms of the Master Theorem a = 1, b = 2, d = 0.
This fits the a = b^d case so worst-case efficiency is Θ(n log n).

---

## Similar Generated Questions

### Master Theorem Application 1 #card
You are given the following recurrence relation:
T(n) = 4T(n/2) + n

Use the Master Theorem to determine the complexity class of this algorithm. Show your work.

**Answer:**
Apply Master Theorem:
a = 4, b = 2, d = 1
Check: 4 compared to 2^1 = 2
Since 4 > 2^1 (a > b^d), we use case 3
T(n) ∈ Θ(n^(log_b a)) = Θ(n^(log_2 4)) = Θ(n^2)

---

### Master Theorem Application 2 #card
Consider the recurrence: T(n) = 3T(n/3) + n^2

Determine the complexity using the Master Theorem.

**Answer:**
a = 3, b = 3, d = 2
Check: 3 compared to 3^2 = 9
Since 3 < 9 (a < b^d), we use case 1
T(n) ∈ Θ(n^d) = Θ(n^2)

---

### Algorithm Pattern Recognition #card
Consider the following algorithm:
```
ALGORITHM findMax(int[] A, int left, int right)
if left == right then
    return A[left]
mid = (left + right) / 2
maxLeft = findMax(A, left, mid)
maxRight = findMax(A, mid+1, right)
return max(maxLeft, maxRight)
```

i) What does this algorithm do?
ii) What algorithmic strategy does it use?
iii) Set up and solve the recurrence relation.

**Answer:**
i) Finds the maximum element in an array
ii) Divide and conquer strategy
iii) C(n) = 2C(n/2) + 1
a = 2, b = 2, d = 0
Since a > b^d (2 > 1), case 3 applies
C(n) ∈ Θ(n^(log_2 2)) = Θ(n)

---

### Warshall's Algorithm Application #card
Given the adjacency matrix:
```
[0 1 1]
[0 0 1]
[1 0 0]
```

Apply Warshall's algorithm to find the transitive closure. Show R^1, R^2, and R^3.

**Answer:**
R^0 = [0 1 1]
      [0 0 1]
      [1 0 0]

R^1 = [0 1 1]
      [0 0 1]
      [1 1 1]

R^2 = [0 1 1]
      [0 0 1]
      [1 1 1]

R^3 = [1 1 1]
      [1 1 1]
      [1 1 1]

---

### Language Reduction Problem #card
L1 reduces to L2 in polynomial time. We know L2 is NP-complete. What can be said about L1?

**Answer:**
L1 is in NP. 

Proof: Since L2 is NP-complete, it has a polynomial-time verifiable certificate. Since L1 reduces to L2 in polynomial time, there exists a reduction function R that converts instances of L1 to instances of L2 in polynomial time. For any string w in L1, we can verify it by: (1) applying R(w) to get an L2 instance, (2) verifying the L2 certificate in polynomial time. The composition of polynomial-time operations is polynomial, so L1 is in NP.

---

### Horspool's Algorithm #card
You are searching for the pattern "BANANA" in a text.

i) Construct the Horspool shift table for alphabet {A, B, N, others}
ii) How many character comparisons would be made when searching in the text "ANANAS_BANANA"?

**Answer:**
i) Shift table:
A = 1 (rightmost A is at position 5, distance from end = 6-5 = 1)
N = 2 (rightmost N is at position 4, distance = 6-4 = 2)
B = 5 (rightmost B is at position 1, distance = 6-1 = 5)
others = 6 (pattern length)

ii) Pattern alignments:
Position 0: Compare 'S' (text[5]) with 'A', fail, shift by 6
Position 6: Compare '_' with 'A', fail, shift by 6
Position 12: Match found after 6 comparisons

---

### Context-Free Grammar Design #card
Design a context-free grammar for the language:
L = {w | w ∈ {0,1}* and w has equal number of 0s and 1s}

**Answer:**
S → ε
S → 0S1S | 1S0S | SS

Alternative solution:
S → ε | 0S1 | 1S0 | SS

---

### Pumping Lemma Application #card
Prove that the language L = {0^n 1^n 0^n | n ≥ 0} is not regular using the pumping lemma.

**Answer:**
Assume L is regular with pumping length p.
Consider w = 0^p 1^p 0^p, which is in L and |w| ≥ p.

By the pumping lemma, w = xyz where:
- |xy| ≤ p
- |y| > 0
- xy^i z ∈ L for all i ≥ 0

Since |xy| ≤ p, both x and y consist only of 0s from the first segment.
Therefore y = 0^k for some k > 0.

Consider xy^2z = 0^(p+k) 1^p 0^p
This has more 0s in the first segment than 1s in the middle, so it is not in L.
This contradicts the pumping lemma, so
