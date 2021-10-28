#ArraysVSLinkedLists
# Arrays Vs. Linked Lists
## Run Times

![image1]

[image1]:https://i.imgur.com/VBACEia.png
![image2]

[image2]:https://i.imgur.com/qzfU6FC.png

From this we can see that Arrays are faster to read but are slower for insertions. Meaning that arrays are much better for random reads and accesses.

Its important to remember that insertions and deletions are O(1)

## Insertions
However linked lists are much better for insertions especially for insertions near the middle as you just have to point the previous to the new object being inserted. 

Whereas arrays every object after the insert would have to be moved down.

## Deletions

What if you want to delete an element? Again, lists are better, because you just need to change what the previous element points. With arrays, everything needs to be moved up when you delete an element.

Unlike insertions, deletions will always work. Insertions can fail sometimes when there's no space left in memory. But you can always delete an element.