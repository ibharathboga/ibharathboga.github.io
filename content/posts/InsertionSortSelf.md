---
title: "InsertionSortSelf"
date: 2023-09-09T11:18:13+05:30
draft: true
---
```python
def isort(values):
	for hpos,hcard in enumerate(values[1:],start = 1):
		for gpos,gcard in enumerate(values[:hpos]):
			if gcard>hcard:
				values[gpos:hpos+1] = [hcard] + values[gpos:hpos]
				break
	return values
```

1. An array containing just one element is already sorted.
2. Insertion sort is an algorithm in which each element from the unsorted part is compared and placed in its correct position within the sorted part.
3. Therefore, insertion sort involves working with two parts: the sorted part and the unsorted part.
4. Consequently, insertion sort requires the existence of these two parts.
5. When given an array, we can consider the first element as part of the sorted section and the remaining elements as part of the unsorted section (due to point 1).
6. Let's consider the first card in the unsorted part. We'll keep track of its value and position as `(hcard, hpos)`. (like we are holding it with our right hand)
7. We traverse through the sorted part from left to right until we find a card greater than the holding card. We mark the position of this greater card as `(gcard, gpos)`.
8. Next, we shift all the cards from `gpos` to `hpos` by one step to make room for the holding card. 	
9. Finally, we place the holding card in the position of `gpos`. 
	```python	
	#small challenge, we eventually reach this stage where we have to put 6.5 before 7
	v = [5, 6, 7, 8, 6.5, 2, 1]

	#index positions
	hpos = 4
	gpos = 2

	#the above line solves the challenge
	v[gpos:hpos+1] = v[hpos] + v[gpos:hpos]
	```
10. We repeat steps 6 to 9 until there are no more cards in the unsorted part.

→ this algorithm works well for small array length