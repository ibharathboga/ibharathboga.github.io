---
title: "SelectionSortSelf"
date: 2023-09-09T16:43:36+05:30
draft: true
---

```python
def selsort(v):
	for index in range(len(v)):
		minpos = index
		for i in range(index,len(v)):
			if v[minpos]>v[i]: minpos = i

		v[minpos],v[index] = v[index],v[minpos]
	return v
```

most basic challenge for this algorithm,  
given an array find position of smallest value in the array

```python
minpos = 0
for i in range(len(v)):
	if v[minpos]>v[i]:
		minpos=i
print(f"smallest value is present at index: {minpos}")
```

intermediary challenge for this algorithm,  
given an array and an index position,  
find the position of smallest value in the subarray that starts from the index position and extends to the end of the array

```python
v = [5, 6, 7, 8, 6.5, 2, 1]

#example:given index
index = 2

minpos = index
for i in range(index,len(v)):
	if v[minpos]>v[i]:
		minpos = i
print(f"smallest value between {index} to {len(v)-1} is present at index: {minpos}")
```

pseudo code for selection sort

```
for indexx from 0 to array.length-1
    find position of smallest value present in subarray, array[indexx:]
    swap the elements at indexx position and smallest value position
```
