Binary search is an algorithm which can be used to find a given element in a sorted array in time `O(log(n))`. It works by delimiting partitions in the array based on the value it find in each iteration.

# How it works

Given a array of size n, the first partition is composed by the entire array, so its boundaries are left (index 0) and right (index n-1). Then the following loop its repeated until these boundaries are either in the same index or even past each other.

- The central index is calculated (`c = l + (r - l) / 2`).
- If the value found in this index is less than the target, then the left boundary is set to `c + 1`, as from `c + 1` to `r` there are only values higher than the one in `c`.
- Otherwise, then the right boundary is set to `r - 1`, as from `l` to `c - 1` there are only values lower than the one in `c`.

# Commentary

Binary search is a relatively simple algorithm, however, most of the problems that require the use of it will ask you to implement a program that has the core concept of a binary search with some modified functionalities needed to solve the problem.