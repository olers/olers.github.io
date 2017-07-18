---
layout: post
title: "LibreOJQuine"
date: 2017-07-18
excerpt: "Orz"
tags: [study, Solution, LibreOJ]
comments: true
---

## Description

写一个程序，使其能输出自己的源代码。
代码中必须至少包含十个可见字符。

## Input

输入文件为空。

## Output

你的源代码。

## Solution

**这题...恩 看程序吧**

```cpp
#include <cstdio>
#include <cstring>
#include <algorithm>

#define MAXN 300

char c[MAXN][MAXN];
int n, ans, m;
int l[MAXN][MAXN];

int main() {
    // freopen("1.in", "r", stdin);
    // freopen("1.out", "w", stdout);
    scanf("%d%d", &n, &m);
    for(int i = 1; i <= n; i++) {
        int tmp = 0;
        while(tmp < m) {
            char ch = getchar();
            while(ch != '.' && ch != '*') ch = getchar();
            tmp++;
            c[i][tmp] = ch;
        }
    }
    // for(int i = 1; i <= n; i++) {
    //     for(int j = 1; j <= m; j++) {
    //
    //         printf("%c", c[i][j]);
    //     }
    // }
    // printf("c[%d][%d] = %c \n", i, m, c[i][m]);
    for(int i = 1; i <= n; i++)
        for(int j = 1; j <= m; j++) {
            if(c[i][j] == '*') continue;
            l[i][j] = j;
            if(c[i][j - 1] == '.' && j - 1 > 0) l[i][j] = l[i][j - 1];
            // printf("l[%d][%d] = %d\n", i, j, l[i][j]);
        }

    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= m; j++) {
            if(c[i][j] == '*') continue;
            int tmp = l[i][j];
            for(int k = i; k; k--) {
                if(c[k][j] == '*') break;
                tmp = std::max(tmp, l[k][j]);
                ans += j - tmp + 1;
            }
        }
    }
    printf("%d\n", ans);
    return 0;
}
/*
6
WWWW*B
WBBBBB
WBWWBB
WBBBBB
WWWBBB
WBBBBB

6 4
....
.***
.*..
.***
...*
.***
*/

```
