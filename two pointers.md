
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

- Right pointer (i) = the scout. It walks through the whole array, examining every element one by one.
- Left pointer (j) = the record-keeper. It only moves when the scout finds something worth keeping. It marks the position where the next "valid" value should be placed.

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

The Key Insight — "Tracking"
right is exploring — it looks at every single element, no matter what.
left is tracking progress — it only advances when something new/valid is found, and it marks where to write the next good value.

So left isn't wasting time re-checking things — it's simply a bookmark that says "this is how far we've built our valid result so far." The gap between left and right is basically "stuff we've already looked at and decided to throw away."

Another Common Use: Move Zeroes to the End
```javascript
function moveZeroes(arr) {
  let left = 0; // tracks where the next non-zero should go

  for (let right = 0; right < arr.length; right++) {
    if (arr[right] !== 0) {
      [arr[left], arr[right]] = [arr[right], arr[left]]; // swap
      left++; // advance the tracker since we placed a valid value
    }
  }

  return arr;
}

console.log(moveZeroes([0, 1, 0, 3, 12])); // [1, 3, 12, 0, 0]
```
Same pattern: right scans everything, left only moves when it finds a non-zero — because left marks "the next empty slot for a good value."

### The Mental Model

| Pointer | Role | Moves when... |
|---|---|---|
| `right` (scout) | Explores every element | Every single iteration |
| `left` (tracker) | Remembers/marks the boundary of valid results | Only when something worthy is found |
