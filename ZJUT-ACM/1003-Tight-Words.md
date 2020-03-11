## Description：

Given is an alphabet `{0, 1, ... , k}` (0 <= k <= 9). We say that a word of length `n` over this alphabet is tight if any two neighbour digits in the word do not differ by more than `1` .

## Input

Input is a sequence of lines, each line contains two integer numbers `k` and `n` (1 <= n <= 100).

## Output

For each line of input, output the percentage of tight words of length n over the alphabet `{0, 1, ... , k}` with `5` fractional digits.

## Sample Input:

```
4 1
2 5
3 5
8 7
```

## Sample Output:

```
100.00000
40.74074
17.38281
0.10130
```

**Solve:**

```c++
#include <iostream>
#include <iomanip>
using namespace std;
float map[2][10]; 
unsigned short i, j, itemp1, itemp2;
int main() {
    int k, n;
    while(cin >> k >> n) {
        if(k <= 1 || n == 1) {
//          cout << setprecision(8) << (double)100.0 << endl;
            cout << "100.00000" << endl;
        } else {
            float rate = 100.00000 / (k + 1);
            for(j = 0; j <= k; j++) { // 第0个位置放置各个元素的概率
                map[0][j] = rate;
            }
            // 第i个位置
            for(i = 1; i < n; i++) {
                itemp1 = i % 2;
                itemp2 = (i + 1) % 2;
                // 放置j元素是 tight word 的概率
                for (j = 0; j <= k; j++) {
                    if (j==0) {
                        map[itemp1][j] = ( map[itemp2][j] + map[itemp2][j+1])/(k+1);
                    }
                    else if (j == k) {
                        map[itemp1][j] = ( map[itemp2][j] + map[itemp2][j-1])/(k+1);
                    }
                    else {
                        map[itemp1][j] = ( map[itemp2][j-1] + map[itemp2][j] + map[itemp2][j+1])/(k+1);
                    }
                }
            }
            rate = 0;
            for(j = 0; j <= k; j++) {
                rate += map[itemp1][j];
            }

            cout << setprecision(7) << rate << endl;
        }
    }
    return 0;
}

```

代码参考链接：[https://github.com/OboBear/ACM4ZJUT/blob/master/1003%20Tight%20words/main.cpp](https://github.com/OboBear/ACM4ZJUT/blob/master/1003%20Tight%20words/main.cpp)
