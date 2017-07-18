---
layout: post
title: "LibreOJQuine"
date: 2017-07-18
excerpt: "Orz"
tags: [study, Solution, LibreOJ]
comments: true
---

### Description

>写一个程序，使其能输出自己的源代码。
代码中必须至少包含十个可见字符。

### Input

>输入文件为空。

### Output

>你的源代码。

### Solution

>**这题...恩 看程序吧**

```cpp
#include <cstdio>

const char *s = "#include <cstdio>%c%cconst char *s = %c%s%c;%c%cint main() {%cprintf(s, 10, 10, 34, s, 34, 10, 10, 10, 10);%c%}";

int main() {
printf(s, 10, 10, 34, s, 34, 10, 10, 10, 10);
}
```
