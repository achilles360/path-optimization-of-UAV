# path-optimization-of-UAV
using travelling salesman problem
AIM:- 

To optimize the path of a rescue unmanned aerial vehicle using dynamic programming approach and branch and bound approach.
The branch and bound approach:- The branch and bound method is an algorithm design paradigm which is used to optimize several combinational problems.
In branch and bound approach every possible permutation is explored in worst case scenario. The time complexity of such algorithm is exponential.
[2]In branch and bound the branching is done to form subset from set and then each subset is analysed by the estimated. Lower bound. The branching is dine in the form of tree where top represent the branching points of the set solution and edge denotes the path between two continuous vertices.
The main role in this approach is the making and reducing the table and calculation of the lower bound which in turn decide which path not to take.
Let us take an example to understand it more better:-



Step-01:

First we will write down the initial cost matrix and then reduce the matrix-

IMAGE

To do so, we will sepertely apply row reduction and column reduction on the matrix.
Row Reduction:
 
Looking at all the rows of the cost matrix one after the other:
•	If the row already has a ‘0’, then there is no need to reduce it.
•	If the row does not have a ‘0’, then we will reduce that particular row.
 
To reduce a given row, we choose the element with least value from that row and then subtract that particular element from each element of that row. By doing this, we will create a ‘0’ in that row.
By doing the above method, we have:
•	Subtract all the elements of row 1 by 6
•	Subtract all the elements of row 2 by 7
•	Subtract all the elements of row 3 by 8
•	Subtract all the elements of row 4 by 4
 
Performing this, we get matrix given below which is now row reduced-

IMAGE

Perform column reduction-
 
Now, consider all the columns of the above row reduced matrix one by one.
•	If the column already contains an entry ‘0’, then there is no need to reduce it.
•	If the column does not contains an entry ‘0’, then reduce that particular column.
 
To reduce such a column, select the least value element from that column and then subtract that particular element from each element of that column. This will create an entry ‘0’ in that column.
 
Following this, we have-
•	There is no need to reduce column-1
•	There is no need to reduce column-2
•	Reduce all the elements of column-3 by 1
•	There is no need to reduce column-4
 
Performing this, we obtain the following matrix which is now column reduced-

IMAGE

Finally, this matrix is now completely reduced as it is row reduced as well as column reduced.
 
Now, Cost of node-1 is calculated by adding all the reduction elements.
Cost(1) = 4 + 5 + 6 + 2 + 1 = 18
 
Step-02:
 
Now, we will consider all other vertices one by one and select the best vertex where we can land upon to minimize the cost of the tour.
 
Choosing to go to vertex-B: Node-2 (Path A → B)
 
•	From the reduced matrix of step-01, M[A,B] = 0
•	Set row-A and column-B to ∞
•	Set M[B,A] = ∞
•	Now, resulting cost matrix is-

IMAAGE

Now, we will reduce this matrix in the same way as we reduced the matrix in step-01 and will find out the cost of node-02.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	Reduce all the elements of row-2 by 13
•	There is no need to reduce row-3
•	There is no need to reduce row-4
 
Performing this, we obtain the following matrix which is now row reduced-

IMAGE

Perform column reduction-
 
•	Reduce all the elements of column-1 by 5
•	We can not reduce column-2 as all elements are ∞
•	There is no need to reduce column-3
•	There is no need to reduce column-4
 
Performing this, we obtain the following matrix which is now column reduced-

IMAGE

Finally, this matrix is now completely reduced as it is row reduced as well as column reduced. 
Now, Cost of node-2 is calculated as-
Cost(2) = cost(1) + Sum of reduction elements + M[A,B]
Cost(2) = 18 + (13 + 5) + 0
Cost(2) = 36
 
Choosing to go to vertex-C: Node-3 (Path A → C)
 
•	From the reduced matrix of step-01, M[A,C] = 7
•	Set row-A and column-C to ∞
•	Set M[C,A] = ∞
•	Now, resulting cost matrix is-

IMAGE

Now, we will reduce this matrix in the same way as we reduced the matrix in step-01 and will find out the cost of node-03.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	There is no need to reduce row-2
•	There is no need to reduce row-3
•	There is no need to reduce row-4
 
Thus, this matrix is already row reduced.
 
Perform column reduction-
 
•	There is no need to reduce column-1
•	There is no need to reduce column-2
•	We can not reduce column-3 as all elements are ∞
•	There is no need to reduce column-4
 
Thus, this matrix is already column reduced as well.
So, the matrix is already completely reduced as it is row reduced as well as column reduced.
 
Now, Cost of node-3 is calculated as-
Cost(3) = cost(1) + Sum of reduction elements + M[A,C]
Cost(3) = 18 + 0 + 7
Cost(3) = 25
 
Choosing to go to vertex-D: Node-4 (Path A → D)
 
•	From the reduced matrix of step-01, M[A,D] = 3
•	Set row-A and column-D to ∞
•	Set M[D,A] = ∞
•	Now, resulting cost matrix is-


IMAGE


Now, we will reduce this matrix in the same way as we reduced the matrix in step-01 and will find out the cost of node-04.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	There is no need to reduce row-2
•	Reduce all the elements of row-3 by 5
•	There is no need to reduce row-4
 
Performing this, we obtain the following matrix which is now row reduced-

IMAGE

Perform column reduction-
 
•	There is no need to reduce column-1
•	There is no need to reduce column-2
•	There is no need to reduce column-3
•	We can not reduce column-4 as all elements are ∞
 
Thus, this matrix is already column reduced.
Finally, this matrix is now completely reduced as it is row reduced as well as column reduced.
 
Now, Cost of node-4 is calculated as-
Cost(4) = cost(1) + Sum of reduction elements + M[A,D]
Cost(2) = 18 + 5 + 3
Cost(2) = 26
 
Thus, we have-
Cost(2) = 36 (for Path A → B)
Cost(3) = 25 (for Path A → C)
Cost(4) = 26 (for Path A → D)
We will choose the node with the lowest cost. Since, Cost for node-3 is lowest, so we prefer to visit node-3.
Thus, We choose node-3 i.e. path A → C
 
Step-03:
Now, we will explore the vertices B and D from node-3.
 
Note-
We will now start from the cost matrix at node-3 which is-

IMAGE

Cost(3) = 25
 
Choosing to go to vertex-B: Node-5 (Path A → C → B)
 
•	From the reduced matrix of step-02, M[C,B] = ∞
•	Set row-C and column-B to ∞
•	Set M[B,A] = ∞
•	Now, resulting cost matrix is-
 
IMAGE

Now, we will reduce this matrix and will find out the cost of node-5.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	Reduce all the elements of row-2 by 13
•	We can not reduce row-3 as all elements are ∞
•	Reduce all the elements of row-4 by 8
 
Performing this, we obtain the following matrix which is now row reduced-

IMAGE

Perform column reduction-
 
•	There is no need to reduce column-1
•	We can not reduce column-2 as all elements are ∞
•	We can not reduce column-3 as all elements are ∞
•	There is no need to reduce column-4
 
Thus, this matrix is already column reduced.
Finally, this matrix is now completely reduced as it is row reduced as well as column reduced.
 
Now, Cost of node-5 is calculated as-
Cost(5) = cost(3) + Sum of reduction elements + M[C,B]
Cost(5) = 25 + (13 + 8) + ∞
Cost(5) = ∞
 
Choosing to go to vertex-D: Node-6 (Path A → C → D)
 
•	From the reduced matrix of step-02, M[C,D] = ∞
•	Set row-C and column-D to ∞
•	Set M[D,A] = ∞
•	Now, resulting cost matrix is-

IMAGE

Now, we will reduce this matrix and will find out the cost of node-6.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	There is no need to reduce row-2
•	We can not reduce row-3 as all elements are ∞
•	We can not reduce row-4 as all elements are ∞
 
Thus, this matrix is already row reduced.
 
Perform column reduction-
 
•	There is no need to reduce column-1
•	We can not reduce column-2 as all elements are ∞
•	We can not reduce column-3 as all elements are ∞
•	We can not reduce column-4 as all elements are ∞
 
Thus, this matrix is already column reduced.
Finally, this matrix is now completely reduced as it is row reduced as well as column reduced.
 
Now, Cost of node-6 is calculated as-
Cost(6) = cost(3) + Sum of reduction elements + M[C,D]
Cost(6) = 25 + 0 + 0
Cost(6) = 25
 
Thus, we have-
Cost(5) = ∞ (for Path A → C → B)
Cost(6) = 25 (for Path A → C → D)
We will choose the node with the lowest cost. Since, Cost for node-6 is lowest, so we prefer to visit node-6.
Thus, We choose node-6 i.e. path C → D
 
Step-04:
 
Now, we will explore the vertex B from node-6.
We will start with the cost matrix at node-6 which is-


IMAGE

Cost(6) = 25
 
Choosing to go to vertex-B: Node-7 (Path A → C → D → B)
 
•	From the reduced matrix of step-03, M[D,B] = 0
•	Set row-D and column-B to ∞
•	Set M[B,A] = ∞
•	Now, resulting cost matrix is-


IMAGE

Now, we will reduce this matrix and will find out the cost of node-7.
 
Perform row reduction-
 
•	We can not reduce row-1 as all elements are ∞
•	We can not reduce row-2 as all elements are ∞
•	We can not reduce row-3 as all elements are ∞
•	We can not reduce row-4 as all elements are ∞
 
Perform column reduction-
 
•	We can not reduce column-1 as all elements are ∞
•	We can not reduce column-2 as all elements are ∞
•	We can not reduce column-3 as all elements are ∞
•	We can not reduce column-4 as all elements are ∞
 
Thus, this matrix is already column reduced.
Finally, this matrix is now completely reduced as it is row reduced as well as column reduced. All the entries have become ∞.
 
Now, Cost of node-7 is calculated as-
Cost(7) = cost(6) + Sum of reduction elements + M[D,B]
Cost(7) = 25 + 0 + 0
Cost(7) = 25
Thus,
Optimal Path is: A → C → D → B → A with cost = 25 units
 



Dynamic programming approach:-
In this approach let us take an initial example.
Let the given set of location be {a,b,c,d…..n} let us take a as an starting point and the end point of the output.

For every other location i (other than a), we find the minimum cost path with a as the starting point, i as the ending point and all vertices appearing exactly once.

 Let the cost of this path be cost(i), the cost of corresponding Cycle would be cost(i) + dist(i, 1) where dist(i, 1) is the distance from i to 1.
 Finally, we return the minimum of all [cost(i) + dist(i, 1)] values

To calculate cost(i) using Dynamic Programming, we require recursive relation in form of sub-problems. Let us define a term C(S, i) be the cost of the minimum cost path visiting each location once, starting at a and ending at i.
Now we should start to analyse the cost of individual sub set starting form the size of 2 then we move on to the size 3 and so . but one condition is necessary in this scenario that a must be present in each of the subset as a is our starting point.

If the size of S=2 then s must be {a , i}.
C(S,i)=dist(a , i)
Else if the size of S is greater than 2
C(S,i)=min{C(S-{i} , j) + dist(j , i)}
Where j belongs to S and J is not equal to i ,  a

For a n locations , we consider n-2 subsets each of size n-1 such that all subsets don’t have nth location in them.  Using the above recurrence relation.
There are at most O(n*2n) subproblems, and each one takes linear time to solve. The total running time is therefore O(n2*2n).
The time complexity of this algorithm though less than that of the basic approach but still is high therefore this algorithm is not suitable for large set of location.
