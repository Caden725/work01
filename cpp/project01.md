---
layout: course_layout
title: "2"
---

# 二維陣列
## a171: APCS 112.01 2.造字程式
### 課程紀錄
先讀入K，Q，R與字串S，然後依序讀入Q組排列P，之後模擬每次操作（O(Q*K) 時間複雜度），然後把每次修改後的新字串記下，最後輸出R行×Q列的結果。
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    
    int K, Q, R;
    if (!(cin >> K >> Q >> R)) return 0;
    
    string S;
    cin >> S;
    
    vector<vector<int>> P(Q, vector<int>(K));
    for (int i = 0; i < Q; ++i) {
        for (int j = 0; j < K; ++j) cin >> P[i][j];
    }   
                                       
    vector<string> results;
    results.reserve(Q);
    for (int i = 0; i < Q; ++i) {
        string newS(K, ' ');
        // P[i][j] 是第 i 次排列給出的第 j 個位置 Pi
        // 題目敘述: 新字串的第 Pi 個字元 = 舊字串的第 i 個字元
        // 假設輸入的 Pi 為 1-based，轉成 0-based
        for (int j = 0; j < K; ++j) {
            int pos = P[i][j] - 1; // convert to 0-based
            if (pos >= 0 && pos < K) newS[pos] = S[j];
        }
        results.push_back(newS);
        S = newS;
    }
    
    // 輸出 R 行，每行 Q 個字元
    for (int r = 0; r < R; ++r) {
        for (int q = 0; q < Q; ++q) {
            // results[q] 長度為 K，通常 R <= K；做保險檢查
            if (r < (int)results[q].size()) cout << results[q][r];
            else cout << ' ';
        }
        cout << '\n';
    }
    return 0;
}
```
![image](https://hackmd.io/_uploads/SJnoC4wCgx.png)
### 心得
我覺得這題的難點是一開始有字串S(長度 K），接下來有Q次排列操作，每次給一個排列P=[P1, P2, ..., PK]最後設定新字串的第Pi個字元=舊字串的第i個字元。
