# 函示與遞迴
## a173: 質數日 (PrimeDay)
### 課程紀錄
    這題是要利用函式來完成植樹的判斷
    
```cpp=
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n) {
  for (int i = 2; i < sqrt(n); i++) {
    if (n % i == 0) {
      return false;
    }
  }
  return true;
}

int main() {
  int n;
  cin >> n;

  int date;
  for (int i = 0; i < n; i++) {
    int digit = 10000000;
    cin >> date;
    int t = date, f = 1;
    while (t > 0) {
      if (!isPrime(t)) {
        f = 0;
        cout << date << " isn't a Prime Day!" << endl;
        break;
      }
      t %= digit;
      digit /= 10;
    }
    if (f == 1) {
      cout << date << " is a Prime Day!" << endl;
    }
  }

  return 0;
}
```
![image](https://hackmd.io/_uploads/SyV427neWl.png)


### 心得
    這題困難點是應該要先判斷小於2，以及函式的呼叫
    
## a174: 合成函數(2)
### 課程紀錄
    這題是利用string來將三個方程式合成
    
```cpp=
#include <bits/stdc++.h>

using namespace std;

int eval() {
    int x, y, z;
    string part;
    cin >> part;
    if (part == "f") {
        x = eval();
        return 2 * x - 3;
    }
    else if (part == "g") {
        x = eval();
        y = eval();
        return 2 * x + y - 7;
    }
    else if (part == "h") {
        x = eval();
        y = eval();
        z = eval();
        return 3 * x - 2 * y + z;
    }
    else {
        return stoi(part);
    }
}

int main() {
    int ans = eval();
    cout << ans;
    return 0;
}
```
![image](https://hackmd.io/_uploads/BJUplwBW-x.png)

### 心得
    這題跟合成函數一就差在多一個方程式以及多一個未知數，再設變數的時候多設定就好。
    

## a175: 二維黑白影像編碼
### 課程紀錄
    目的就是算出有幾個黑色的點
    
```cpp=
#include <bits/stdc++.h>
using namespace std;

string str;
int num, idx = -1;
int matrix(int n) {
  idx++;
  if (str[idx] == '0') {
    return 0;
  } 
  else if (str[idx] == '1') {
    return n * n;
  } 
  else if (str[idx] == '2') {
    int cnt = 0;
    for (int i = 0; i < 4; i++) {
      cnt += matrix(n / 2);
    }
    return cnt;
  }
}

int main() {
  cin >> str;
  cin >> num;
  int output = matrix(num);
  cout << output;

  return 0;
}
```
![image](https://hackmd.io/_uploads/Hyk7JuHZ-g.png)
