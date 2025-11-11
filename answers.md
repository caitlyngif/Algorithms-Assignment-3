# CMPS 2200 Assignment 3
## Answers

**Name:** Caitlyn Gifford


Place all written answers from `assignment-03.md` here for easier grading.

**1a** Take the largest power of 2 that is less than or equal to N. Subtract this value from N, and then repeat the process until N is 0. *The specific denominations of coins used is either 0 or 1 since we are trying to find the least amount of coins possible. For example, if the coin has value 2^i = 2^3 = 8, then that is equal to 2^(i-1) + 2^(i-1) = 2^2 + 2^2 = 8. Instead of using two of the denomination lower of coins with value 2^(i-1), we can just use one coin of 2^i. 

**1b** This solution has the greedy choice property because it is locally optimal, as it takes the largest power of 2 that is <= N. It also has the optimal substructure property because after you choose the largest power of 2 first, then the remaining amount is N - 2^i. The denominations of coins remaining are all powers of 2, so the subproblem is the same as the original. 

**1c** The problem states that there are k dominations of values 2^0, 2^1, 2^2, ... , 2^k. There are log base 2 (N) distinct powers of 2 up to N (k = log base 2(N)). Therefore, there are about log base 2 (N) + 1 denominations. At each step, there are constant-time operations (checking if 2^i <= N -> subtracting that value from N -> move to i = i - 1). Therefore, work = O(log N) since there are at most log N denominations of coins that can be used to make N. Since every iteration depends on the previous, the algorithm is sequential. Therefore, span = O(log N).

**2a** Arbitrary set of denominations: {2, 5, 6}. Suppose N = 10. Using the largest denomation <= N, you would choose 6, and 10-6 = 4. The next largest denomation <= N is 2, and you would use two of those coins to = 4. This uses 3 coins total. The optimal solution would be two coins, using just 5 + 5 to = N.

**2b** The optimal substructure property is true if an optimal solution can be constructed from optimal solutions of smaller subproblems. This holds true in this example because the optimal amount of coins for N depends on having the optimal amount of coins for N - Di (Di being the denomination chosen firt). Going further, the optimal amount of coins for N - Di depends on having the optimal amount of coins for N - Dj (Dj being the denomation chosen second). 

**2c** I would use a bottom-up approach. To do this, I would create an empty table C[] holding N + 1 indexes, where the ith index will hold the minimum number of coins needed to make change for amount i. Initialize the 0th index to hold value 0. For index i of 1 to N, check if each arbitrary denomination d is less than or equal to the index. If it is, then update the index to be the lowest value of C(i) or 1 + C(i-d). The work is O(n * d) since we check all d denominations until N. The span is O(n) since the table is built sequentially.