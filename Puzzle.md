# Puzzle
The puzzle was a neat challenge. When we ran it, it showed:
```
Do you like puzzles? I do
Consider the following puzzle
Spend exactly 100 dollars and buy exactly 100 animals.
Dogs cost 15 dollars, cats cost 1 dollar, and mice cost 25 cents each.
You have to buy at least one of each. How many of each should you buy?
dogs: $15, cats: $1, mice $0.25
```
it asked for the number of each animal. You can solve it in two ways: the easy way and the math way.
## Easy way
Brute force each animal until it shows us 'Congrats'.
```
for  i  in  range(1, 100):
	for  j  in  range(1, 100):
		for  k  in  range(1, 100):
			if  check(i, j, k):
				print("dogs:", i, "cats:", j, "mice:", k)
```
`dogs: 3 cats: 41 mice: 56`
## Math way
Given that:
 - d: the number of dogs
 - c: the number of cats
 - m: the number of mice
 
The problem provides the following constraints:
 1.   The total cost of the animals must be exactly 100 dollars.
 2.   The total number of animals must be exactly 100.
 3.   At least one of each type of animal must be bought.

We can write the constraints as equations: 
15d+1c+0.25m=100
d+c+m=100

From the second equation we can solve for c in terms of d and m:
 ```
 d + c + m = 100
 c = 100 - d - m
 ```
 Substitute `c = 100 - d - m` into the first equation:
 `15d + 1(100-d-m) + 0.25 = 100` 
 Simplify the equation:
 ```
 15d + 100 - d - m + 0.25 = 100
 14d - 0.75m + 100 = 100
 14d - 0.75m = 0
 d = 0.75m/14
 m = 14d/0.75
```
 for `d` to be an integer, `0.75m/14` must be an integer. This means `m` must be a multiple of `4`.
d = 0.75*(4m) / 14
 
 For `m` to be an integer, `14d/0.75`  must be an integer. This means d must be a multiple of `3`.
 m = 14(3d)/0.75
 ```
 if d = 3,
 m = (14*3)/0.75 == 56
 c = 100 - 3 - 56 = 41
 Since c >= 1, d >= 1, m >= 1
 3 + 41 + 56 = 100
 (15*3) + (41*1) + (56*0.25) == 100 
 Therefore, the solution is:
 -   Number of dogs (d): 3
-   Number of cats (c): 41
-   Number of mice (m): 56
 ```
