# Fish
I was wondering why it was named fish.

The challenge gave us a python source code
```python
old_flag  =  "7b}tF13Ea{7$_4K5lUg_r"

def  go_fish(arr, size):
	random.seed(0xdead)
	n  =  random.randint(0, 2**31)
	for  i  in  range(0, size-1):
		arr[i], arr[i+1+(n  % (size  - (i+1)))] =  arr[i+1+(n  % (size  - (i+1)))], arr[i]
	return  "".join(arr)
```
After looking for a bit in google and searching I found a shuffle algorithm called
[Fisher-Yates](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle).

To reverse the Fisher-Yates shuffle, we'll use the shuffled indices to reconstruct the original array. Here’s how to do it step by step:

1.  Generate the shuffled indices using the Fisher-Yates algorithm.
2.  Create a mapping from the shuffled position to the original position.
3.  Use this mapping to rearrange the characters in the shuffled string back to their original positions.

```python
import random
old_flag =  "7b}tF13Ea{7$_4K5lUg_r"

# Fisher-Yates shuffle algorithm
def  go_fish(arr, size):
	random.seed(0xdead)
	n = random.randint(0, 2**31)
	for i in  range(0, size-1):
		arr[i], arr[i+1+(n % (size - (i+1)))] = arr[i+1+(n % (size - (i+1)))], arr[i]
# return "".join(arr)
	return arr
	
# For any shuffle algorithm the only we can reverse it by creating an indices list
indices =  list(range(0, len(old_flag)))
print(indices)
# Then shuffle the indices list
shuffled_indices = go_fish(indices, len(indices))
print(shuffled_indices)
# Then take the index of i in shuffled indices
print(old_flag)
for i in  range(0, len(old_flag)):
	print(old_flag[shuffled_indices.index(i)], end="")
```
