# special-pythogoreas-triplet-
Problem Statement
A Pythagorean triplet is a set of three natural numbers 
𝑎
a, 
𝑏
b, and 
𝑐
c such that:

𝑎
2
+
𝑏
2
=
𝑐
2
a 
2
 +b 
2
 =c 
2
 
For a given integer 
𝑁
N, you need to check if there exists a Pythagorean triplet such that the sum of 
𝑎
+
𝑏
+
𝑐
=
𝑁
a+b+c=N. If such a triplet exists, you should return the maximum product 
𝑎
×
𝑏
×
𝑐
a×b×c of the triplet. If no such triplet exists, return -1.

Input Format:
The first line contains an integer 
𝑇
T, representing the number of test cases.
The next 
𝑇
T lines contain one integer 
𝑁
N, representing the value for each test case.
Output Format:
For each test case, print the maximum product 
𝑎
×
𝑏
×
𝑐
a×b×c for the Pythagorean triplet whose sum is 
𝑁
N. If no such triplet exists, print -1.

Constraints:
1
≤
𝑇
≤
1000
1≤T≤1000
1
≤
𝑁
≤
1
0
5
1≤N≤10 
5
 
Example
Input:
Copy code
2
12
4
Output:
diff
Copy code
60
-1
Explanation:
For 
𝑁
=
12
N=12:

We find a Pythagorean triplet 
(
3
,
4
,
5
)
(3,4,5) such that:
3
2
+
4
2
=
5
2
and
3
+
4
+
5
=
12
3 
2
 +4 
2
 =5 
2
 and3+4+5=12
The product of the triplet is:
3
×
4
×
5
=
60
3×4×5=60
For 
𝑁
=
4
N=4:

There is no Pythagorean triplet whose sum is 4, so the output is -1.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
// Project Euler #9: Special Pythagorean triplet
// A what triplet, you say?
//
// https://www.hackerrank.com/contests/projecteuler/challenges/euler009
//

#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

int main()
{
    const int M = 3000;
    int cache[M + 1];

    for (int i = 0; i <= M; ++i)
        cache[i] = -1;

    for (int a = 1; a < M; ++a)
    {
        int a_a = a * a;

        for (int b = a + 1; b <= M - a; ++b)
        {
            int c_c = a_a + b * b;

            if (c_c % 4 == 3) continue;

            int c = (int) sqrt(c_c);
            if (c * c != c_c) continue;

            int p = a + b + c;
            if (p > M) break;

            int abc = a * b * c;
            if (cache[p] < abc) cache[p] = abc;
        }
    }

    int t;
    scanf("%d",&t);
    for(int a0 = 0; a0 < t; a0++){
        int n;
        scanf("%d",&n);


        printf("%d\n", cache[n]);
    }
    return 0;
}
