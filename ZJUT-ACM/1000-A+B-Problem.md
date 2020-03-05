#### Description：

Calculate a + b

#### Input:

The input will be consist of a series of pairs of integers a and b,separated by a space, one pair of integers per line, 0 0 means the end of the input, and do not need to output.

输入一系列由空格隔开的 a、b 组成的整数对，每行一对整数，0 0 表示结束输入，并且不需要输出。

#### Output:

For each pair of input integers a and b you should output the sum of a and b in one line,and with one line of output for each line in input.

每行 a、b 的和对应着每行 a、b 的整数对，并且一行输入一行输出。

#### Sample Input:

```
1 5
0 0
```

#### Sample Output:

```
6
```

**Solve:**

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() {
    int a, b;
    vector<int> results; // c++向量容器，存储 a、b 的和

    cout << "Please input a series of pairs of integers:" << endl;
    cin >> a >> b;

    while(a != 0 || b != 0) {
        results.push_back(a + b);
        cin >> a >> b;
    }

    cout << "The results is:" << endl;
    for (int i = 0; i < results.size(); i++) { // 遍历c++向量容器
        cout << results[i] << endl;
    }

    return 0;
}
```

