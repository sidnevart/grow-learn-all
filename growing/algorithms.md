# Алгоритмы и структуры данных

> **Цель:** Закрыть gap между production-интуицией и формальной алгоритмической глубиной. Для top-собеседований (Google, Netflix, Stripe, top-вузы).
> **Время:** 3-4 месяца (по 1-2 часа в день)
> **Уровень:** От medium до hard на LeetCode

---

## Что именно учить

### 1. Основы (неделя 1-2)

**Темы:**
- Time/Space Complexity (Big-O)
- Arrays, Strings, Hash Maps
- Two Pointers, Sliding Window
- Basic Sorting (QuickSort, MergeSort)
- Binary Search

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.006 — Lecture 1-5 | Видео + notes | 5 часов | [ocw.mit.edu/6-006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) |
| LeetCode Patterns — Two Pointers | Практика | 10 задач | [leetcode.com](https://leetcode.com) |
| Big-O Cheatsheet | Шпаргалка | 1 час | [bigocheatsheet.com](https://www.bigocheatsheet.com) |

**Задачи для старта:**
```
1. Two Sum (LeetCode 1)
2. Valid Anagram (LeetCode 242)
3. Contains Duplicate (LeetCode 217)
4. Product of Array Except Self (LeetCode 238)
5. Maximum Subarray (LeetCode 53)
6. 3Sum (LeetCode 15)
7. Container With Most Water (LeetCode 11)
```

### 2. Структуры данных (неделя 3-4)

**Темы:**
- Linked List (singly, doubly, circular)
- Stack, Queue, Deque
- Tree (BST, AVL, Red-Black — concepts)
- Heap / Priority Queue
- Trie
- Union-Find (Disjoint Set)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.006 — Lectures 6-10 | Видео + notes | 6 часов | [ocw.mit.edu/6-006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) |
| LeetCode Explore — Linked List | Практика | 10 задач | [leetcode.com/explore](https://leetcode.com/explore) |
| Visualgo | Визуализация | 2 часа | [visualgo.net](https://visualgo.net) |

**Задачи:**
```
Linked List:
8. Reverse Linked List (LeetCode 206)
9. Merge Two Sorted Lists (LeetCode 21)
10. Reorder List (LeetCode 143)
11. Linked List Cycle (LeetCode 141)

Stack/Queue:
12. Valid Parentheses (LeetCode 20)
13. Min Stack (LeetCode 155)
14. Daily Temperatures (LeetCode 739)

Tree:
15. Invert Binary Tree (LeetCode 226)
16. Maximum Depth of Binary Tree (LeetCode 104)
17. Same Tree (LeetCode 100)
18. Subtree of Another Tree (LeetCode 572)
19. Lowest Common Ancestor (LeetCode 236)
20. Validate BST (LeetCode 98)

Heap:
21. Kth Largest Element (LeetCode 215)
22. Find Median from Data Stream (LeetCode 295)
23. Merge K Sorted Lists (LeetCode 23)

Trie:
24. Implement Trie (LeetCode 208)
25. Word Search II (LeetCode 212)
```

### 3. Graphs (неделя 5-6)

**Темы:**
- BFS, DFS
- Dijkstra, Bellman-Ford
- Topological Sort
- Union-Find (advanced)
- Minimum Spanning Tree (Kruskal, Prim)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.006 — Lectures 13-17 | Видео + notes | 6 часов | [ocw.mit.edu/6-006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) |
| William Fiset — Graph Algorithms | YouTube | 4 часа | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLDV1Zeh2NRsDGO4--qE8yF4SbKfVsx4mM) |
| LeetCode Graph Tag | Практика | 15 задач | [leetcode.com/tag/graph](https://leetcode.com/tag/graph) |

**Задачи:**
```
26. Number of Islands (LeetCode 200)
27. Clone Graph (LeetCode 133)
28. Course Schedule (LeetCode 207) — Topological Sort
29. Course Schedule II (LeetCode 210)
30. Pacific Atlantic Water Flow (LeetCode 417)
31. Rotting Oranges (LeetCode 994) — BFS
32. Word Ladder (LeetCode 127) — BFS
33. Network Delay Time (LeetCode 743) — Dijkstra
34. Cheapest Flights Within K Stops (LeetCode 787) — Bellman-Ford
35. Alien Dictionary (LeetCode 269) — Topological Sort
36. Graph Valid Tree (LeetCode 261) — Union-Find
```

### 4. Dynamic Programming (неделя 7-8)

**Темы:**
- Memoization
- Tabulation
- 0/1 Knapsack, Unbounded Knapsack
- Longest Common Subsequence
- Edit Distance
- House Robber pattern
- DP on Trees

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.006 — Lectures 19-21 | Видео + notes | 4 часа | [ocw.mit.edu/6-006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) |
| NeetCode — DP Patterns | YouTube | 3 часа | [youtube.com/watch?v=HAA8mgxolv8](https://www.youtube.com/watch?v=HAA8mgxolv8) |
| DP Patterns | Статья | 1 час | [leetcode.com/discuss/general-discussion/458695/dynamic-programming-patterns](https://leetcode.com/discuss/general-discussion/458695/dynamic-programming-patterns) |

**Задачи:**
```
37. Climbing Stairs (LeetCode 70)
38. House Robber (LeetCode 198)
39. House Robber II (LeetCode 213)
40. Coin Change (LeetCode 322)
41. Longest Increasing Subsequence (LeetCode 300)
42. Longest Common Subsequence (LeetCode 1143)
43. Edit Distance (LeetCode 72)
44. Word Break (LeetCode 139)
45. Combination Sum IV (LeetCode 377)
46. Decode Ways (LeetCode 91)
47. Unique Paths (LeetCode 62)
48. Target Sum (LeetCode 494)
49. Interleaving String (LeetCode 97)
50. Regular Expression Matching (LeetCode 10) — Hard
```

### 5. Advanced (неделя 9-12)

**Темы:**
- Segment Tree / Fenwick Tree (Binary Indexed Tree)
- Advanced Graphs (A*, Floyd-Warshall)
- Bit Manipulation
- Advanced DP
- Greedy Algorithms
- Backtracking

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.046J (Design and Analysis of Algorithms) | Курс | 10 лекций | [ocw.mit.edu/6-046j](https://ocw.mit.edu/courses/6-046j-design-and-analysis-of-algorithms-spring-2015/) |
| CP-Algorithms | Статьи | — | [cp-algorithms.com](https://cp-algorithms.com) |
| LeetCode Hard | Практика | 20 задач | [leetcode.com](https://leetcode.com) |

**Задачи:**
```
51. Maximum XOR of Two Numbers (LeetCode 421) — Trie + Bit
52. Median of Two Sorted Arrays (LeetCode 4) — Binary Search
53. LRU Cache (LeetCode 146) — Design
54. LFU Cache (LeetCode 460) — Design
55. Insert Delete GetRandom O(1) (LeetCode 380) — Design
56. Range Sum Query — Mutable (LeetCode 307) — Segment Tree
57. Count of Smaller Numbers After Self (LeetCode 315) — Fenwick Tree
58. N-Queens (LeetCode 51) — Backtracking
59. Sudoku Solver (LeetCode 37) — Backtracking
60. Burst Balloons (LeetCode 312) — DP
61. Longest Valid Parentheses (LeetCode 32) — Stack/DP
62. Trapping Rain Water (LeetCode 42) — Two Pointers/Stack
63. Largest Rectangle in Histogram (LeetCode 84) — Stack
64. Sliding Window Maximum (LeetCode 239) — Deque
65. Design Search Autocomplete System (LeetCode 642) — Trie + Heap
66. Serialize and Deserialize Binary Tree (LeetCode 297) — Design
67. Design In-Memory File System (LeetCode 588) — Design
68. Text Justification (LeetCode 68) — String manipulation
69. Minimum Window Substring (LeetCode 76) — Sliding Window
70. Find Median from Data Stream (LeetCode 295) — Two Heaps
71. Count of Range Sum (LeetCode 327) — Merge Sort / Fenwick
72. Split Array Largest Sum (LeetCode 410) — Binary Search
73. K-th Smallest in Lexicographical Order (LeetCode 440) — Hard
74. Cherry Pickup (LeetCode 741) — 3D DP
75. Frog Jump (LeetCode 403) — DP with HashSet
```

---

## Книги

| Книга | Автор | Для чего | Где взять |
|-------|-------|----------|-----------|
| Introduction to Algorithms (CLRS) | Cormen et al. | Библия, reference | [Amazon](https://amazon.com) / PDF |
| Algorithm Design | Kleinberg & Tardos | Интуиция, доказательства | [Amazon](https://amazon.com) |
| Cracking the Coding Interview | Gayle Laakmann McDowell | Собеседования, задачи | [Amazon](https://amazon.com) |
| Elements of Programming Interviews | Aziz et al. | Задачи по темам | [Amazon](https://amazon.com) |
| Competitive Programmer's Handbook | Antti Laaksonen | CP, алгоритмы | [cses.fi/book](https://cses.fi/book/book.pdf) — **бесплатно** |

---

## Курсы

| Курс | Платформа | Время | Стоимость | Ссылка |
|------|-----------|-------|-----------|--------|
| MIT 6.006 | MIT OCW (бесплатно) | 25 лекций | Бесплатно | [ocw.mit.edu/6-006](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/) |
| MIT 6.046J | MIT OCW (бесплатно) | 20 лекций | Бесплатно | [ocw.mit.edu/6-046j](https://ocw.mit.edu/courses/6-046j-design-and-analysis-of-algorithms-spring-2015/) |
| Princeton Algorithms (Part I & II) | Coursera | 12 недель | Бесплатно (audit) | [coursera.org/learn/algorithms-part1](https://www.coursera.org/learn/algorithms-part1) |
| Stanford CS161 | YouTube | 20 лекций | Бесплатно | [youtube.com](https://www.youtube.com/playlist?list=PLoROMvodv4rNswM7WuyuJigZJcCF7j6zN) |
| Tim Roughgarden — Algorithms | Coursera / Stanford | 4 части | Бесплатно (audit) | [coursera.org/specializations/algorithms](https://www.coursera.org/specializations/algorithms) |

---

## Mock Interviews

| Ресурс | Что | Стоимость | Ссылка |
|--------|-----|-----------|--------|
| Pramp | Бесплатные mock interviews | Бесплатно | [pramp.com](https://www.pramp.com) |
| interviewing.io | Anonymous mock with engineers | $150-300 | [interviewing.io](https://interviewing.io) |
| Exponent | PM + tech mock | $100-200 | [tryexponent.com](https://www.tryexponent.com) |
| LeetCode Discuss | Peer mock | Бесплатно | [leetcode.com/discuss](https://leetcode.com/discuss) |
| Telegram — Russian IT community | Найти друга для mock | Бесплатно | Поиск по чатам |

---

## Output: как показать прогресс

**Каждые 25 задач:**
- Скриншот LeetCode profile → LinkedIn / Habr
- Написать 1 пост: "25 задач LeetCode: что я узнал про X"

**Каждые 50 задач:**
- Сделать mock interview
- Написать 1 пост с разбором любимой задачи

**После 100 задач:**
- Попробовать Google Kick Start / Codeforces Div 2
- Написать: "100 задач LeetCode: мой путь от medium к hard"

---

## Трекер: 12-недельный план

| Неделя | Фокус | Задачи | Output |
|--------|-------|--------|--------|
| 1 | Big-O, Arrays, Two Pointers | 1-7 | Пост: "Big-O за 1 неделю" |
| 2 | Sliding Window, Sorting | 8-14 | Mock interview #1 |
| 3 | Linked List, Stack, Queue | 15-24 | Пост: "Linked List vs Array в production" |
| 4 | Tree, Heap | 25-35 | Mock interview #2 |
| 5 | Graphs BFS/DFS | 36-42 | Пост: "Graphs в distributed systems" |
| 6 | Advanced Graphs | 43-50 | Mock interview #3 |
| 7 | DP Basics | 51-58 | Пост: "DP: от рекурсии к табуляции" |
| 8 | DP Advanced | 59-65 | Mock interview #4 |
| 9 | Design Problems | 66-70 | Пост: "Design LRU Cache: алгоритмы в production" |
| 10 | Bit Manipulation, Advanced | 71-75 | Mock interview #5 |
| 11 | Review weak areas | — | Пост: "100 задач LeetCode: итоги" |
| 12 | Mock interviews intensive | — | 3 mock interviews |

---

**Последнее обновление:** 16 May 2026
