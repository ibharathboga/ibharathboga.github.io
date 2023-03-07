---
title: "CodeChef Problems Week 1"
date: 2023-02-27T08:21:51+05:30
draft: true
---
[CodeChef Problem: HOWMANYMAX](https://www.codechef.com/problems/HOWMANYMAX)  
[Reference Solution](https://www.codechef.com/viewsolution/83811725)
```python
#Solution
value = input()
#value = "11100"
reducedValue = value[0]
for v in value:
    if v != reducedValue[-1]:reducedValue+=v
    else: continue
#print(reducedValue)

maxCount = int
if len(reducedValue) == 1:
    maxCount =1
else:        
    maxCount = reducedValue.count("01")
    if reducedValue[0] == "1": maxCount+=1
    if reducedValue[-1] == "0": maxCount+=1

print(maxCount)
```

```python
#explanation view
value = "11100"
for i in range(len(value)):
    if value[i] == "1":
        print(f"{i+1} > {i+2}")
    else:
        print(f"{i+1} < {i+2}")
```
