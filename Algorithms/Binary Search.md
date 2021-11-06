### Binary Search Algorithm by Jon Bentley

Time Complexity: O(log n)

- This algorithms is used for searching.
- It's prerequisite is that the array to be searched must be sorted.

Here is a great explanation for the same: [MyCodeSchool YT Link](https://www.youtube.com/watch?v=j5uXyPJ0Pew).

Problem 1: [LeetCode](https://leetcode.com/problems/binary-search).
Make sure that you checkout the [solution](https://leetcode.com/problems/binary-search/solution/) for the above problem.

Problem 2: [LeetCode](https://leetcode.com/problems/first-bad-version).

Problem 3: [LeetCode](https://leetcode.com/problems/search-insert-position).

**Points to remember:**
- low = 0 and high = n-1
- low <= high
- array must be sorted
- Here is a helpful tip to quickly prove the correctness of your binary search algorithm during an interview. We just need to test an input of size 2. Check if it reduces the search space to a single element (which must be the answer). If not, your algorithm will never terminate.

**Something interesting:**
- [A common bug in Binary Search Algorithm](https://ai.googleblog.com/2006/06/extra-extra-read-all-about-it-nearly.html)