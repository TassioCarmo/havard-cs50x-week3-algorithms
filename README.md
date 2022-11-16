# Introduction to algorithms concepts
## What did i learn?

## Search

Think an array as a bunch of close lockets, because  the computer can’t look at all of the elements at once with an outside view. Instead, a computer can only to look at them one at a time

<img src = "https://cs50.harvard.edu/x/2022/notes/3/lockers.png">


## Running time

how long an algorithm takes to run given some size of input.

### BIg O

“on the order of” something, higher bound or worst case scenario for the algorithms in relation to steps it takes to do something
 

<img src = "https://cs50.harvard.edu/x/2022/notes/3/time_to_solve_zoomed_out.png">

Common running times
- O(n^2) size of array * size of inner array
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

- O(n) one by one, constant number of steps
- Ω(1) you can find it on the first position (if you are lucky)

```
For each door from left to right
    If number is behind door
        Return true
Return false
```
## Binary Search

- O(\log n) half and half 
- Ω(1) you can find it on the first position (if you are lucky)

only work if the numbers are sorted tho

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

Why would you waste your time as a dev sort before search? it would be pointless to doit because you are already seeing the data

because if your problem is a Google-like problem where you have more than just one user who's searching for more than just one website page,  you problably should incur the cost up front and sort the whole thing for every subsequent request thereafter to be faster, because it's going to be algorithm of binary search instead of linear search which is going to be way fewer steps than doing linear search multiple times

But at the end of the day you should always ask yourself as a devolper what is your most precious resource? 

Is it time to run the code? Is it time to write the code? Is it the amount of memory the computer is using? 

## Structs

data type, or data structure which is our own data type,
typedef struct tells the compiler that we’re defining our own data structure

```
typedef struct
{
    string name;
    string number;
}
person;
```
**encapsulation** is the idea that related data is grouped together, and here we’ve encapsulated two pieces of information, name and number into the same data structure. The color of a pixel, with red, green, and blue values, might also be well-represented by a data structure as well.


## Sorting 

### Selection sort 
- O(n^2/2) or O(n^2)
- Ω(n^2) 
 
because when n is big enough when dealing with potency it doesn't matter
find the smallest and swap with the swap with th e number in the beginning

```
5 2 7 4 1 6 3 0
              ^

0 | 2 7 4 1 6 3 5
```

```
For i from 0 to n–1
    Find smallest number between numbers[i] and numbers[n-1]
    Swap smallest number with numbers[i]
```
### Bubble sort 

- O(n)
- Ω(n)
- or theta of n

compare numbers next to each other 

```
5 2 7 4 1 6 3 0
^ ^             

2 5|7 4 1 6 3 0
```

```
Repeat n-1 times
    For i from 0 to n–2
        If numbers[i] and numbers[i+1] out of order
            Swap them
    If no swaps
        Quit
        
   Set swap counter to a non-zero value. 
      • Repeat until the swap counter is 0: •
        Reset swap counter to 0. 
        • Look at each adjacent pair
        if two adjacent elements are not in order, swap them and add one to the swap counter
```
### Recursion

 Recursion is the ability for a function to call itself:
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
 We’re using the same “search” algorithm for each half. This seems like a cyclical process that will never end, but we’re actually changing the input to the function and dividing the problem in half each time, stopping once there are no more doors left.
void draw(int n);
  ```
int main(void)
{
    int height = get_int("Height: ");

    draw(height);
}
  
void draw(int n)
{
    //simple base case that will break the recursion
    if (n <= 0)
    {
        return;
    }
  
    draw(n - 1);
  
    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}
```
What is a piramd of height 4? a piramid of height 3 + one more roll, same logic applies to recursion 
```
#
##
###

#
##
###
####

```
### Merge sort 

uses more memory but it's faster
- O(log n)
- Ω(n \log n)

```
If only one number
  Quit
Else
    Sort left half of number
    Sort right half of number
    Merge sorted halves
```

How the algorithm works

```   
 5 2 7 4 1 6 3 0

    We start by looking at the first half, which is a list of size 4:

    5 2 7 4

        We’ll have to sort the left half, which is a list of size 2:

        5 2

            The left half is size 1, so we’re done, and the right half is also size 1, so we can merge both halves together:

            2 5

        Now we’ll need to sort the right half:

        7 4

            Again, we’ll merge both of these halves together, by taking the smallest element from each list

            4 7

        Now we’ve sorted both halves, each of size 2, and can merge them together:

        2 5 | 4 7
        ^     ^

          5 | 4 7
          ^   ^
        2

          5 |   7
          ^     ^
        2 4

            |   7
                ^
        2 4 5

        2 4 5 7

    We’ll repeat this for the right half, another list of size 4:

    1 6 3 0

        Sorting the left half gives us 1 6, and the right half merges to 0 3.
        We’ll merge those with:

        1 6 | 0 3
        ^     ^

        1 6 |   3
        ^       ^
        0

          6 |   3
          ^     ^
        0 1

          6 |
          ^
        0 1 3 

        0 1 3 6


    
    2 4 5 7 | 0 1 3 6
^         ^

2 4 5 7 |   1 3 6
^           ^
0

We’ll move the next smallest number, 1, down, and look at the next number in that list:

2 4 5 7 |     3 6
^             ^
0 1

This time, the 2 is the next smallest, so we’ll move that down, and repeat this process:

  4 5 7 |     3 6
  ^           ^
0 1 2

  4 5 7 |       6
  ^             ^
0 1 2 3

    5 7 |       6
    ^           ^
0 1 2 3 4

      7 |       6
      ^         ^
0 1 2 3 4 5

      7 |
      ^
0 1 2 3 4 5 6

        |
0 1 2 3 4 5 6 7


```
