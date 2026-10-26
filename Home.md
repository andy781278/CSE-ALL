- [ ] CSE 120
	- [ ] Lecture 1
	- [ ] Midterm Oct 27 NEXT TUE
	- [x] Project Oct 23 FRI ✅ 2026-10-23
	- [x] HW Oct 22 THUR ✅ 2026-10-23
- [ ] CSE 167
	- [x] Lecture 3 ✅ 2026-10-26
	- [x] HW Oct 26 NEXT MON ✅ 2026-10-26
- [ ] CSE 110
	- [x] Lecture 0
	- [x] Midterm Oct 23 FRI ✅ 2026-10-23
	- [ ] Sprint 1 2 weeks ish

# LeetCode Plan for Internship Assessments

Six weeks at about 1 hour a day in Python, about 70 problems, ordered by topic, ending with timed mock assessments.

## Daily routine

1. Solve 2 new problems, 25 minutes each, with a timer running.
2. If you have no working approach after 25 minutes, read the solution, close it, and write it yourself from memory.
3. Spend the last 10 minutes re-solving one problem from 2 days earlier without notes.
4. Mark a problem done only after you solve it alone. Problems you needed a solution for stay unchecked until you redo them.

On Sunday each week, do a timed set of 3 problems from that week in 90 minutes.

## Weeks 1 to 6

### Week 1 (Oct 26 to Nov 1): arrays, hashing, two pointers

- Two Sum
- Contains Duplicate
- Valid Anagram
- Top K Frequent Elements
- Product of Array Except Self
- Longest Consecutive Sequence
- Valid Palindrome
- Two Sum II
- 3Sum
- Container With Most Water
- Valid Sudoku

### Week 2 (Nov 2 to Nov 8): sliding window, stack, binary search

- Best Time to Buy and Sell Stock
- Longest Repeating Character Replacement
- Permutation in String
- Valid Parentheses
- Min Stack
- Daily Temperatures
- Evaluate Reverse Polish Notation
- Binary Search
- Search a 2D Matrix
- Koko Eating Bananas
- Find Minimum in Rotated Sorted Array
- Search in Rotated Sorted Array
- Time Based Key-Value Store

### Week 3 (Nov 9 to Nov 15): linked lists, trees

- Reverse Linked List
- Merge Two Sorted Lists
- Linked List Cycle
- Remove Nth Node From End of List
- Reorder List
- LRU Cache
- Invert Binary Tree
- Maximum Depth of Binary Tree
- Same Tree
- Diameter of Binary Tree
- Lowest Common Ancestor of a Binary Search Tree
- Binary Tree Level Order Traversal
- Validate Binary Search Tree
- Kth Smallest Element in a BST

### Week 4 (Nov 16 to Nov 22): grids, graphs, heaps

- Spiral Matrix
- Rotate Image
- Set Matrix Zeroes
- Game of Life
- Max Area of Island
- Rotting Oranges
- Pacific Atlantic Water Flow
- Surrounded Regions
- Clone Graph
- Course Schedule
- Kth Largest Element in an Array
- K Closest Points to Origin
- Task Scheduler

### Week 5 (Nov 23 to Nov 29): backtracking, dynamic programming

- Subsets
- Combination Sum
- Permutations
- Word Search
- Climbing Stairs
- House Robber
- Coin Change
- Unique Paths
- Longest Increasing Subsequence
- Longest Common Subsequence
- Word Break
- Decode Ways
- Partition Equal Subset Sum

### Week 6 (Nov 30 to Dec 6): intervals, design, mock assessments

- Merge Intervals
- Insert Interval
- Non-overlapping Intervals
- Design Underground System
- Design Browser History
- Mock assessment 1: 4 problems in 90 minutes, mixed topics
- Mock assessment 2: 4 problems in 90 minutes, mixed topics
- Mock assessment 3: a LeetCode virtual contest

The grid problems in Week 4 and the design problems in Week 6 are closest to the game-board and multi-part questions Riot candidates have reported.

## Python to memorize

- List: `append`, `pop`, slicing, `reverse`, list comprehensions, `[[0] * cols for _ in range(rows)]` for a grid
- Dict and set: `get(key, default)`, `in`, `items()`, set `add` and `remove`
- Sorting: `sorted(xs, key=lambda x: x[1])`, `reverse=True`
- `collections`: `deque` (`append`, `popleft`), `Counter`, `defaultdict(list)`
- `heapq`: `heappush`, `heappop`, `heapify`; push negative values for a max-heap
- `bisect`: `bisect_left`, `bisect_right`
- Strings: `split`, `join`, `isalnum`, `lower`, `ord`, `chr`
- Grid directions: `for dr, dc in [(1, 0), (-1, 0), (0, 1), (0, -1)]`
- Recursion: `@functools.cache` for memoized DP, `sys.setrecursionlimit` for deep DFS