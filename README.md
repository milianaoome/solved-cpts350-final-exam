Download Link: https://assignmentchef.com/product/solved-cpts350-final-exam
<br>
Take-home Final Exam:

Solving linear Diophantine constraints using labeled graphs

(Total=160 pts. 7 days. For students who planned, at the beginning of this semester, to take exams at Access Center, you may text me 509-338-5089 for extended time for completing this take home final exam. Start now before it is too late.)

This set of exam problems is designed to test your capabilities in learning and understanding new algorithms, implementing them and generalizing them. Make sure that you give yourself a lot of time in digesting the videos that I am going to upload. You may use Python, C, C++, or Java to do the implementation. All the work must be your own; collaboration is prohibited. Please do not search on the Internet and try to find any help — you are going to waste your time — I design the exam so that it is googling-proof.

<ol>

 <li>As we have learned in cpts350 this semester, NP is the class of problems that can be solved by nondeterministic algorithms in polynomial time. In particular, NP-complete problems are the hardest ones in NP. Currently, it is open whether we have efficient solutions to those problems. That is, many researchers are still trying to find (deterministic) polynomial time algorithms to solve those NPcomplete problems, or at least to find practically efficient algorithms for them. Such efforts would lead to successfully cracking RSA, which is known in NP (but we do not know whether cracking RSA, i.e., factorizing a large number, is NP-complete). There is a well-known NP-complete problem, called linear Diophantine (written LD), which seeks nonnegative integer solutions to a linear constraint system <em>Q </em>over multiple variables <em>x</em><sub>1</sub><em>,</em>··· <em>,x<sub>k</sub></em>, for some <em>k</em>; e.g.,</li>

</ol>

<sup></sup>2<em>x</em><sub>1 </sub>+ <em>x</em><sub>2 </sub>+ 15 = 0

3<em>x</em>1 − 4<em>x</em>2 <em>&gt; </em>18

(1)

<sub></sub><em>xx</em><sub>11 </sub>+ 3<em>&gt; </em>15<em>x</em><sub>2 </sub><em>&lt; </em>27

The example LD instance shown in (1) has two nonnegative integer variables <em>x</em><sub>1 </sub>and <em>x</em><sub>2 </sub>and four constraints. Notice that the range of the variables is unbounded; hence, you can not assume that they are in 32-bits unsigned ! Please stare at the example for 10 minutes and see how you would design an algorithm to find whether it has solutions and if it has, how you would come up with a solution. Suddenly, you find that all the knowledge you learned in the course won’t give you any ideas that are even remotely close to designing such an algorithm. You need a ground breaking idea. (Do not even try to solve LD using equationsolving skills (called Newton elimination) you learned in high school; variables in those high school equations are of real values and do not apply here.)

<ol>

 <li>(10pts) Formally, an LD-instance <em>Q </em>is given as, for some <em>k </em>and <em>m</em>,</li>

</ol>

#<sub>1 </sub>0

(2)

<em>C</em><em>m</em>1<em>x</em>1 + ··· + <em>C</em><em>mkx</em><em>k </em>+ <em>C</em><em>m </em>#<em>m </em>0

where all the <em>x<sub>j</sub></em>’s are nonnegative integer variables (called unknowns), and the following are all the <em>parameters</em>:

<ul>

 <li>all the coefficients <em>C<sub>ij</sub></em>’s, which are integers (positive, negative, zero), and</li>

 <li>all the numbers <em>C<sub>i</sub></em>’s, which are <strong>nonnegative integers</strong>, and, finally,</li>

 <li>all the #<em><sub>i</sub></em>’s, each of which is in {<em>&gt;,&lt;,</em>=}.</li>

</ul>

What are the the values of the <em>m</em>, the <em>k </em>and the parameters for the example LD instance shown in (1) ?

<ol start="2">

 <li>(10pts) Any algorithm that solves the LD problem is to take an instance <em>Q </em>in (2) as the algorithm’s input, and to return yes (along with a solution) if the instance has a nonnegative integer solution in the unknowns <em>x</em><sub>1</sub><em>,</em>·· <em>,x<sub>k</sub></em>, and to return no if otherwise. What is the size of the input? (Hint: the size of number 4.6 billions is roughly 32. why?)</li>

 <li>(10pts) Tell me why the following is NOT an algorithm to solve the LD problem:</li>

</ol>

input an instance <em>Q </em>in (2) for each nonnegative integer tuple (<em>v</em><sub>1</sub><em>,</em>··· <em>,v<sub>k</sub></em>) check whether (<em>x</em><sub>1 </sub>= <em>v</em><sub>1</sub><em>,</em>··· <em>,x<sub>k </sub></em>= <em>v<sub>k</sub></em>) satisfies all the constraints in <em>Q</em>.

If yes, return yes along with solution (<em>x</em><sub>1 </sub>= <em>v</em><sub>1</sub><em>,</em>··· <em>,x<sub>k </sub></em>= <em>v<sub>k</sub></em>).

The remaining of the exam asks you to implement a brilliant idea in solving the LD problem: representing each linear constraint (such as 2<em>x</em><sub>1 </sub>− 3<em>x</em><sub>2 </sub>+ 4 = 0) in an instance <em>Q </em>using a labeled graph (i.e., a finite automaton). Hence, since there are <em>m </em>constraints in the instance <em>Q</em>, you need then implement a graph composition algorithm to convert the <em>m </em>graphs into one final graph. Then, you perform basic graph search on the final graph to finally solve the LD problem.

<ol start="4">

 <li>(60pts) Watch the take-home-final-exam-help videos, where I presented the aforementioned brilliant ideas (which were invented decades ago by some of our brightest ancestors in algorithms) and you take notes while watching (otherwise, you can not do problems 6 and 7). Make sure that you fully understand the ideas. In this project, you are going to implement those ideas to solve an instance <em>Q </em>in three variables and with 2 equations. Being Diophantine, the variables are of nonnegative integers. As I said, you may use Python, C, C++, or Java to do the implementation. I do not ask you to design the algorithm, instead, I present the algorithm’s design, and you need only implement the algorithm. You need turn-in working code and prepare for a demo.</li>

</ol>

Preparation 1.

Herein, an equation is in the form of

<em>C</em><sub>1</sub><em>x</em><sub>1 </sub>+ <em>C</em><sub>2</sub><em>x</em><sub>2 </sub>+ <em>C</em><sub>3</sub><em>x</em><sub>3 </sub>+ <em>C </em>= 0                                                (3)

where constants <em>C</em><sub>1</sub><em>,C</em><sub>2</sub><em>,C</em><sub>3 </sub>are integers (positive,negative, zero), and constant <em>C </em>is <strong>nonnegative</strong>. Hence, for instance, 3<em>x</em><sub>1 </sub>+ 0<em>x</em><sub>2 </sub>− 4<em>x</em><sub>3 </sub>− 17 = 0 is not an equation in the above form. However, equivalently, −3<em>x</em><sub>1 </sub>− 0<em>x</em><sub>2 </sub>+ 4<em>x</em><sub>3 </sub>+ 17 = 0 is in the above form.

For the equation in (3), we define

<em>.                        </em>(4)

(Exercise: For the aforementioned equation −3<em>x</em><sub>1 </sub>−0<em>x</em><sub>2 </sub>+4<em>x</em><sub>3 </sub>+17 = 0, what is the value of <em>C</em><sub>max</sub>?)

<strong>Implement </strong>a function that returns <em>C</em><sub>max </sub>from the description of an equation in (3), and use the above Exercise to test your function.

Preparation 2.

For a constant <em>C </em>≥ 0, we use binary representation for <em>C</em>. For instance, if <em>C </em>= 34, then in binary, <em>C </em>= 100010. In this case, we use

<em>b</em>6<em>b</em>5<em>b</em>4<em>b</em>3<em>b</em>2<em>b</em>1

for it, with <em>b</em><sub>6 </sub>= 1<em>,b</em><sub>5 </sub>= <em>b</em><sub>4 </sub>= <em>b</em><sub>3 </sub>= 0<em>,b</em><sub>2 </sub>= 1<em>,b</em><sub>1 </sub>= 0. Herein, we define <em>K<sub>C </sub></em>= 6 (the number of bits needed to represent <em>C</em>). In particular when <em>C </em>= 0, we let

<em>K<sub>C </sub></em>= 0.

Hence, for 1 ≤ <em>i </em>≤ <em>K<sub>C</sub></em>, the <em>b<sub>i </sub></em>is defined as above. However, for <em>i </em>= <em>K<sub>C </sub></em>+ 1, the <em>b<sub>i </sub></em>is now defined as 0. (Exercise: Let <em>C </em>= 18. What is the value of <em>K<sub>C</sub></em>?

what is the value of <em>b</em><sub>6</sub>? what is the value of <em>b</em><sub>4</sub>?)

<strong>Implement </strong>a function that returns the value <em>K<sub>C </sub></em>from a given constant <em>C </em>≥ 0. <strong>Implement </strong>a function that returns the value <em>b<sub>i </sub></em>from a given constant <em>C </em>≥ 0 and <em>i</em>, noticing that the <em>i </em>shall be in the range of 1 ≤ <em>i </em>≤ <em>K<sub>C </sub></em>+ 1.

Algorithm 1. Equation to labeled graph (automaton)

We now construct a finite automaton <em>M </em>from the description of the equation in (3).

The input alphabet of <em>M </em>contains exactly eight input symbols, where each symbol is in the form of (<em>a</em><sub>1</sub><em>,a</em><sub>2</sub><em>,a</em><sub>3</sub>) with <em>a</em><sub>1</sub><em>,a</em><sub>2</sub><em>,a</em><sub>3 </sub>∈ {0<em>,</em>1}. (Hence, an input symbol is a triple of three Boolean values.)

A state in <em>M </em>is a pair of values: [<em>carry,i</em>], where

−<em>C</em>max ≤ <em>carry </em>≤ <em>C</em>max<em>,</em>

recalling that <em>C</em><sub>max </sub>is defined in (4), and 1 ≤ <em>i </em>≤ <em>K<sub>C </sub></em>+ 1.

The initial state in <em>M </em>is [<em>carry </em>= 0<em>,i </em>= 1]. The accepting state is [<em>carry </em>= 0<em>,i </em>= <em>K<sub>C </sub></em>+ 1].

For all states [<em>carry,i</em>] and [<em>carry</em><sup>0</sup><em>,i</em><sup>0</sup>] and all input symbols (<em>a</em><sub>1</sub><em>,a</em><sub>2</sub><em>,a</em><sub>3</sub>), the following is true: (<em>a</em><sup>1</sup><em>,a</em><sup>2</sup><em>,a</em><sup>3</sup>)      <sup>0</sup><em>,i</em><sup>0</sup>] is a transition in <em>M </em>(i.e., <em>M </em>moves from state [<em>carry,i</em>]  −→          [<em>carry</em>

[<em>carry,i</em>] to state [<em>carry</em><sup>0</sup><em>,i</em><sup>0</sup>] on reading input symbol (<em>a</em><sub>1</sub><em>,a</em><sub>2</sub><em>,a</em><sub>3</sub>)) if and only if the following is true:

Let <em>R </em>= <em>C</em><sub>1</sub><em>a</em><sub>1 </sub>+ <em>C</em><sub>2</sub><em>a</em><sub>2 </sub>+ <em>C</em><sub>3</sub><em>a</em><sub>3 </sub>+ <em>b<sub>i </sub></em>+ <em>carry</em>. Then, <em>R </em>is divisible by 2, and. Furthermore, if 1 ≤ <em>i </em>≤ <em>K<sub>C</sub></em>, then <em>i</em><sup>0 </sup>= <em>i </em>+ 1, else <em>i</em><sup>0 </sup>= <em>i</em>. (You shall use the functions <strong>implemented </strong>above to implement this step; e.g., to compute the <em>b<sub>i</sub></em>.)

<strong>Implement </strong>a function that returns the finite automaton <em>M </em>from the description of an equation in (3). Notice that you shall use a graph as the data structure of the automaton <em>M</em>. (The automata we constructed are all deterministic by definition.)

Algorithm 2. Cartesian product of two labeled graphs (i.e., two automata)

Now we are given a system of 2 equations over three variables <em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,x</em><sub>3</sub>, where we use <em>E</em><sub>1</sub>(<em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,x</em><sub>3</sub>) and <em>E</em><sub>2</sub>(<em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,x</em><sub>3</sub>) to indicate the two equations and recall that the equations are in the form of (3). Suppose that, using the Algorithm 1 presented earlier, we obtain finite automata <em>M</em><sub>1 </sub>and <em>M</em><sub>2 </sub>from the two equations respectively. Then, we need construct a finite automaton M that is the Cartesian product of <em>M</em><sub>1 </sub>and <em>M</em><sub>2</sub>. You need watch the aforementioned take-home-final-exam-help videos on how to implement the Cartesian product algorithm.

<strong>Implement </strong>a function that returns the M from the <em>M</em><sub>1 </sub>and the <em>M</em><sub>2 </sub>(which are computed using the function implemented in Algorithm 1 from descriptions of the two equations). Again, the resulting automaton M uses a graph as its data structure.

Final step.

If there is no path from the initial to the accepting in M, then the equation system does not have solutions, else we can find a solution by using DFS on the graph of the M (from the initial to the accepting while collecting the sequence of input symbols on the path). Notice that you shall reverse the sequence and then convert it into digit before you output the solution. I will sketch a little more detail of this step. Suppose that the following sequence of input symbols is collected on a path from the initial to the accepting: (1<em>,</em>0<em>,</em>1)<em>,</em>(0<em>,</em>1<em>,</em>1)<em>,</em>(1<em>,</em>0<em>,</em>0)<em>,</em>(1<em>,</em>1<em>,</em>0)

then, what is the solution to the equation system? it is 1011, 0101, 1100 (how did I do it? I got 1011 by picking the first bit from each input symbol in the sequence!). After reversing them, I have 1101, 1010, 0011. Then I convert them into digits: 13, 10, 3. Hence, the solution is actually <em>x</em><sub>1 </sub>= 13<em>,x</em><sub>2 </sub>= 10<em>,x</em><sub>3 </sub>= 3.

Please also <strong>implement </strong>this final step and use the following two to test your code:

T1. The following equation system does not have nonnegative integer solutions:

3<em>x</em><sub>1 </sub>− 2<em>x</em><sub>2 </sub>+ <em>x</em><sub>3 </sub>+ 5 = 0

6<em>x</em><sub>1 </sub>− 4<em>x</em><sub>2 </sub>+ 2<em>x</em><sub>3 </sub>+ 9 = 0

T2. The following equation system does have nonnegative integer solutions (and manually verify that the solution found after you run your code indeed satisfies the following constraints):

3<em>x</em><sub>1 </sub>− 2<em>x</em><sub>2 </sub>− <em>x</em><sub>3 </sub>+ 3 = 0

6<em>x</em><sub>1 </sub>− 4<em>x</em><sub>2 </sub>+ <em>x</em><sub>3 </sub>+ 3 = 0

You shall turn in code and screenshots of running results on the two test cases. You may also be requested for a demo by running your code on a new test case provided by your TAs.

<ol start="5">

 <li>(10pts) Analyze the worst case time complexity for the algorithm in 4. Recall that your complexity function is on the size of input.</li>

 <li>(10pts) Sketch how to generalize the algorithm that you implemented (for two constraints and three variables) to a general LD instance <em>Q </em>in (2).</li>

 <li>(10pts) Argue why the generalized algorithm runs in exponential time (on the size of input).</li>

 <li>(40pts) Describe an application that your generalized algorithm in 6 above can be used.</li>

</ol>

Grading criteria: Probs 1, 2, 3: correctness. Prob 4: if your code is perfectly working, you get full score. Otherwise, partial credit may be given. Prob 5: the lower (but still correct) the better. Prob 6: correctness and readability. I dont need a detaile write-up. Prob 7: write up your reasoning. Prob 8: at least two pages and will be graded on relevance and quality of writing.

<strong>I will not accept any hand-written solutions! Please type.</strong>