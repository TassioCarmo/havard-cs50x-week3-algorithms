# Introduction to algorithms
## What did i learn?

### Search

See an array as a bunch of close lockets, because the computer can't see what it's in the with going inside

<img src = "https://cs50.harvard.edu/x/2022/notes/3/lockers.png">

## algorithms quality

Better designed doesn't use up too much memory, and it isn't redundant

## Running time

### BIg O

“on the order of” something,  higher bound or in other words worst case scenario for the algorithms in relation to steps
 

<img src = "https://cs50.harvard.edu/x/2022/notes/3/time_to_solve_zoomed_out.png">

common running times
- O(n^2)
- O(n \log n)
- O(n) one by one
- O(\log n) half / half
- O(1)

On the order of n over 2 is pretty much the same when n gets really large as being equivalent to big O of n itself

### Ω Omega

lower bound/best case scenario

- Ω(n^2)
- Ω(n \log n)
- Ω(n)
- Ω(\log n)
- Ω(1)

### Θ Theta 

when both big O and Omega are the same

- Θ(n^2)
- Θ(n \log n)
- Θ(n)
- Θ(\log n)
- Θ(1)

## Linear search

one by one, constant number of steps O(n) and Ω(1) you can find it on the first position

```
For each door from left to right
    If number is behind door
        Return true
Return false
```
## Binary Search

half and half   O(\log n) and Ω(1)
only work if the numbers are sorted

```
If no doors
    Return false
If number behind middle door
    Return true
Else if number < middle door
    Search left half
Else if number > middle door
    Search right half

```

### Searching vs sorting and Searching

just one it's pointless to sort because you are already seeing the data

if your problem is a Google-like problem where you have more than just one user who's searching for more than just one website page, probably you should incur the cost up front and sort the whole thing because every subsequent request thereafter is going to be faster, faster, faster because it's going to be algorithm of binary search, binary search, binary search that's going to add up to be way fewer steps than doing linear search multiple times

what is your most precious resource? 

Is it time to run the code? Is it time to write the code? Is it the amount of memory the computer is using? 
