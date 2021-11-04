#Divide-And-Conquer

# Divide & Conquer

## Farm Land Example

Suppose you're a farmer with a plot of land.

![d&c1]

[d&c1]: https://i.imgur.com/E6Ha99n.png

We want to divide this farm evenly into square plots. We want the plots to be as big as possible. So none of the below examples will work.

![d&c2]

[d&c2]: https://i.imgur.com/AKK36Cn.png

So. How do we figure out the largest square fize you can use for a plot of land? We use a strategy called Divide and Conquer. D&C algorithms are recursive algorithms. To solve a problem using D&C, there are two steps we need to follow:

1. Figure out the base case. This should be the simplest possible case.
2. Divide or decrease your problem until it becomes the base case.

Let's use D&C to find the solution to this problem. What is the largest square size we can use?

First we figure out the base case. The easiest case would be if one side was a multiple of the other side.

![d&c3]

[d&c3]: https://i.imgur.com/hj48wvt.png

Suppose one side is 25meters and the other side if 50m. Then the largest box you can use is 25m x 25m. You need two of those boxes to divide up the land.

Now you need to figure out the recursive case. This is where D&C comes in. According to D&C, with every recursive call, you have to reduce your problem. How do you reduce the problem here?
Let's start by marking out the biggest boxes you can use.

![d&c4]

[d&c4]: https://i.imgur.com/2asYUV1.png

You can fit two 640 x 640 boxes in there, and there's some land still left to be divided. From here we then apply the same algorithm to the section thats left over.

![d&c5]

[d&c5]: https://i.imgur.com/FwtAT8H.png

![d&c6]

[d&c6]: https://i.imgur.com/7tDGiJX.png

And that leaves you with a smaller segment, 400 x 240 m.

![d&c7]

[d&c7]: https://i.imgur.com/LntXc4B.png
And you can draw a box on that to get an even smaller segment, 240 x 160 m.

![d&c8]

[d&c8]: https://i.imgur.com/iH3RLKp.png

And then repeat to get an even smaller segment.

![d&c9]

[d&c9]: https://i.imgur.com/s3oljc5.png
Now we have reached our best case of 80! 80 being a factor of 160. If you split up this segment using boxes, you dont have anything left over!

![d&c10]

[d&c10]: https://i.imgur.com/zicsgOR.png
So, for the original farm, the biggest plot size you can use is 80 x 80 m.

![d&c11]

[d&c11]: https://i.imgur.com/ND5Y2tt.png

## Array of Numbers Example
You're given an array of number. You have to add up all the numbers and return the total. It's pretty easy to do this with a loop:

```python
def sum(arr):
	total = 0
	for x in arr:
		total += x
	return total
	
print sum([1, 2, 3, 4])
```

But how would we do this with a recursive function?

### Step 1
Figure out the base case. What's the simplest array you could get? Think about the simplest case. If you gat an array with 0 or 1 elements, then its pretty easy to sum.