# 字串
## 課程紀錄
### a163: APCS 106.03 1.秘密差
```cpp=
#include <iostream>
#include <cmath>  

#include <string>
using namespace std;

int main() {
    string X;
    cin >> X;

    int A = 0, B = 0;
    for (int i = 0; i < X.size(); i++) {
        int digit = X[i] - '0';
        if ((i + 1) % 2 == 1)  
            B += digit;
        else                
            A += digit;
    }

    cout << abs(A - B) << endl;
    return 0;
}
```
![image](https://hackmd.io/_uploads/rJr2_6Npgl.png)







### a063: 文字反序
```cpp=
#include <iostream>
#include <string>
#include <algorithm>  // for reverse()

using namespace std;

int main() {
    string s;
    getline(cin, s);   // 讀取一整行（包含空格）

    reverse(s.begin(), s.end());  // 字串反轉

    cout << s << endl;
    return 0;
}

```
![image](https://hackmd.io/_uploads/SkdIt646xx.png)

### a003: 提款卡密碼
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    string s;
    while (cin >> s) {
        if (s.size() != 7) continue;
        for (int i = 0; i < 6; ++i) {
            cout << abs(s[i] - s[i+1]);
        }
        cout << '\n';
    }
    return 0;
}
```   
![image](https://hackmd.io/_uploads/Sk6QWji2xg.png)

## 心得

### a164: APCS 114.01 2.字串操作
```cpp=
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string s;
    int k;
    cin >> s;
    cin >> k;

    for (int i = 0; i < k; i++) {
        int op;
        cin >> op;

        if (op == 0) {  
            // 兩兩交換
            for (int j = 0; j < s.size(); j += 2)
                swap(s[j], s[j + 1]);

        } else if (op == 1) {  
            // 兩兩排序
            for (int j = 0; j < s.size(); j += 2)
                if (s[j] > s[j + 1])
                    swap(s[j], s[j + 1]);

        } else if (op == 2) {  
            // 完美重排
            int n = s.size();
            string t = "";
            string left = s.substr(0, n / 2);
            string right = s.substr(n / 2);
            for (int j = 0; j < n / 2; j++) {
                t += left[j];
                t += right[j];
            }
            s = t;
        }
    }

    cout << s << endl;
    return 0;
}
```
![image](https://hackmd.io/_uploads/B1tL9a4axe.png)


## 心得
第一行輸入一個字串 S (2 ≤ S ≤ 100) ，字串長度保證為偶數。接下來一行輸入一個正整數 k，接下來有 k 行，每一行有一個數字，種類為 0,1,2。
