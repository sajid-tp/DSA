
### Inward (converging) two-pointer traversal   
It is a technique where two pointers start at opposite ends of a sorted array (or string) — one at the beginning (left), one at the end (right) — and move toward each other based on a condition, until they meet or cross. Because the data is sorted, each pointer movement eliminates a whole range of pairs that couldn't possibly be the answer, letting you solve problems in O(n) time instead of checking every pair with nested loops (O(n²)).

```javascript
function isPalindrome(str) {
  let left = 0;
  let right = str.length - 1;

  while (left < right) {
    if (str[left] !== str[right]) {
      return false; // mismatch found
    }
    left++;   // move inward from the start
    right--;  // move inward from the end
  }

  return true; // pointers met/crossed without mismatch
}

console.log(isPalindrome("racecar")); // true
console.log(isPalindrome("hello"));   // false
```
