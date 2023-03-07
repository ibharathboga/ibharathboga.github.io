---
title: "CodeChef Problems Week 1"
date: 2023-03-06T04:04:48+05:30
draft: false
---

[CodeChef Problem VCS](https://www.codechef.com/problems/VCS)
```python
# cook your dish here
for _ in range(int(input())):
    n,m,k = map(int,input().split())
    ignored = {int(num) for num in input().split()}
    tracked = {int(num) for num in input().split()}
    
    ti = len(ignored & tracked) 
    """
    i did, 
    utui = len(range(1,n+1) - (ignored | tracked))
    but we can also do,
    """
    utui = n - len((ignored | tracked))
    
    print(f"{ti} {utui}")
```

temp 
