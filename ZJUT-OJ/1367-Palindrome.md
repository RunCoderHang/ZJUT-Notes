## Description：

There are many character strings.You should judge which one is the palindrome .

## Input:

There are including several test cases.Every case occupies one line.Every line has one character string .the end line is 0,and this line needn’t to be processed.

## Output:

If the Character string is palindrome output “Yes”,else “No”.

## Sample Input:

```
12321
abbab
0
```

## Sample Output:

```
Yes
No
```

## Solve:

**双指针**

```c++
#include <iostream>
#include <string.h>
using namespace std;
bool isPalinedrome(string s) {
    int length = s.size();
    int start = 0, end = length - 1;
    while(start < end) {
        if(s[start] == s[end]) {
            start++;
            end--;
        } else {
            return false;
        }
    }
    return true;
}
int main() {
    string s;
    while(cin >> s) {
        if(s == "0") break;
        if(isPalinedrome(s)) {
            cout << "Yes" << endl;
        } else {
            cout << "No" << endl;
        }
    }
    return 0;
}

```
