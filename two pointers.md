
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

### Unidirectional traversal
In unidirectional traversal, both pointers start at the same spot (usually index 0) and both move forward — but at different speeds/conditions. They never cross paths from opposite ends like the "inward" pattern; instead, one pointer explores ahead, and the other pointer stays behind, marking where the "good" data should go.

Think of it like this:  

Right pointer (i) = the scout. It walks through the whole array, examining every element one by one.
Left pointer (j) = the record-keeper. It only moves when the scout finds something worth keeping. It marks the position where the next "valid" value should be placed.

The left pointer is basically saying: "Everything before me is confirmed good. I'm the boundary between what's finished and what's still being checked."

Remove Duplicates from Sorted Array
```javascript
function removeDuplicates(arr) {
  let left = 0; // tracks the position of the last unique element

  for (let right = 1; right < arr.length; right++) {
    if (arr[right] !== arr[left]) {
      left++;                 // make room for a new unique value
      arr[left] = arr[right]; // record it
    }
    // if arr[right] === arr[left], it's a duplicate — just skip it (right moves on)
  }

  return left + 1; // number of unique elements
}

console.log(removeDuplicates([1, 1, 2, 2, 3]))
```
