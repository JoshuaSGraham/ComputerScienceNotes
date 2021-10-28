#Arrays
# Arrays
Using an array means that all of your tasks are stored contiguously (right next to each other) in memory.

This means should we have 3 objects stored and want to store another in the array if the next memory slot along is already in use. We then have to move the whole array to another place in memory where all four objects can be stored contiguously.
This repeats for each time we want to store more stuff and there is no available memory next to our array contiguously.

An easy fix to this is to just reserve memory in advance. Say 10 spaces so that we dont need to move the array until those 10 spaces are used up that we reserved.

This does have downsides however:
* You may not need the extra slots that you have reserved, and then thta memory will be wasted. You might not be using it, but no one else can use it either.
* You may add more than 10 items to the array and have to move it anyway.