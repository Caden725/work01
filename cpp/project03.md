# STL
## a122: 山寨版磁力蜈蚣
### 課程紀錄
    這題在之前就做過了，指示駐次改用動態陣列vector改寫
```cpp=
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int n;
    while (cin >> n) { 
        vector<int> a(n);
        for (int i = 0; i < n; i++) cin >> a[i];

        for (int i = 0; i < n; i++) {
            if (i) cout << " ";
            cout << a[i];
        }
        cout << endl;

       
        while (a.size() > 1) {
            a.erase(a.begin());

            reverse(a.begin(), a.end());

            for (int i = 0; i < (int)a.size(); i++) {
                if (i) cout << " ";
                cout << a[i];
            }
            cout << endl;
        }
    }
    return 0;
}

```
![image](https://hackmd.io/_uploads/S1S4oOey-g.png)

### 心得
    vector相較於一般陣列arr來的方便，因為不需要在一開始就設定好大小，可以隨時將數據丟進去處存。然後在使用Vector的時候要記得加標頭檔，要不然跑不出來。

## a145: Sunny會的遊戲
### 課程紀錄
    使用者輸入一個數字n之後，形成一個由n個數字組成的圈，每次往同一個方向5個數字之後，輸出那個數字，並且從圈中刪除那個數字，直到結束。
```cpp=
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n;
    cin >> n;

    vector<int> people;
    for (int i = 1; i <= n; i++)
        people.push_back(i);

    int idx = 0; 
    const int step = 5; 

    vector<int> out; 

    while (!people.empty()) {
       
        idx = (idx + step - 1) % people.size();
        out.push_back(people[idx]);
        people.erase(people.begin() + idx);

        
        if (people.empty()) break;
        if (idx == people.size()) idx = 0; 
    }

    for (int i = 0; i < n; i++) {
        if (i) cout << " ";
        cout << out[i];
    }
    cout << endl;

    return 0;
}
```
![image](https://hackmd.io/_uploads/ry1oLFxkZl.png)
### 心得
    這題我認為最困難的點是4和5個字咒語後的規律，在小畫家畫三輪就找到規律直接破題了。

## a081: Rails
### 課程紀錄
    這題就是想像成火車進站(堆疊)，然後可以從頂端彈出夥從b出站，然後一旦出站就不能返回。

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
  int n;
  while (cin >> n) {
    if (n == 0) {
      break;
    }
    int t;
    cin >> t;
    while (t != 0) {
      vector<int> train;
      stack<int> station;
      train.push_back(t);
      for (int i = 1; i < n; i++) {
        cin >> t;
        train.push_back(t);
      }
      int num = 0;
      for (int i = 1; i <= n; i++) {
        station.push(i);
        while (!station.empty() && station.top() == train[num]) {
          station.pop();
          num++;
        }
      }
      if (num == n) {
        cout << "Yes" << endl;
      } else {
        cout << "No" << endl;
      }
      cin >> t;
    }
    cout << endl;
  }

  return 0;
}
```
![image](https://hackmd.io/_uploads/S12FlxXlbe.png)
### 心得
    這題我認為的困難點是測資進入的順序判斷，寫完之後還要用while重複執行才能判斷               
## a083: 丟紙牌
### 課程紀錄

```cpp=
#include <bits/stdc++.h>
using namespace std;

int main() {
  queue<int> q;
  int n;
  while (cin >> n) {
    if (n == 0)
      break;
    for (int i = 1; i <= n; i++) {
      q.push(i);
    }
    cout << "Discarded cards: ";
    while (q.size() > 2) {
      cout << q.front() << ", ";
      q.pop();
      q.push(q.front());
      q.pop();
    }
    cout << q.front() << endl;
    q.pop();
    cout << "Remaining card: " << q.front() << endl;
    q.pop();
  }
}
```
![image](https://hackmd.io/_uploads/SyBuRgQl-e.png)
