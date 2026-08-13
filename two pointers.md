
### Inward (converging) two-pointer traversal   
It is a technique where two pointers start at opposite ends of a sorted array (or string) — one at the beginning (left), one at the end (right) — and move toward each other based on a condition, until they meet or cross. Because the data is sorted, each pointer movement eliminates a whole range of pairs that couldn't possibly be the answer, letting you solve problems in O(n) time instead of checking every pair with nested loops (O(n²)).
