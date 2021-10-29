#Selection-Sort

# Selection Sort
Selection sort uses both [[Arrays]] and [[LinkedLists]]

## Premise
Suppose you have a bunch of music on your computer. For each artist, you have a play count.

![table1]

[table1]: https://i.imgur.com/hgBRTMm.png
We want to sort this list from most to least played, allowing us to rank our favorite artists. How would we do this?

## Solution
One way to go through the list and find the most-played artist. Add that artist to a new list looking something like this:

![table2]

[table2]: https://i.imgur.com/6fFU2WB.png
Repeating this over and over, finding the next-most played artists.
![table3]

[table3]: https://i.imgur.com/KQPcVnt.png
Keep doing this and we end up with a sorted list.
![table4]

[table4]: https://i.imgur.com/kjufzHE.png

![runtime1]

[runtime1]: https://i.imgur.com/HFH1k2t.png

#Selection-Sort-Code-python
## Code Implementation
```py
def findSmallest(arr):
	smallest = arr[0]
	smallest_index = 0
	for i in range (1, len(arr)):
		if arr[i] < smallest:
			smallest = arr[i]
			smallest_index = i
	return smallest_index
	
def selectionSort(arr):
	newArr = []
	for i in range(len(arr)):
		smallest = findSmallest(arr)
		newArr.append(arr.pop(smallest))

	return selectionSort([5, 3, 6, 2, 10])
```