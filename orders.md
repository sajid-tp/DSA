### O(1) — Constant Time

Definition:  
O(1) means the amount of work performed by an algorithm does not increase as the input size n increases. It performs a fixed/constant amount of work.

Example — Accessing an array element:  
```javascript
const arr = [10, 20, 30, 40, 50];

console.log(arr[2]);
```
Whether the array contains 5 elements or 1,000,000 elements, accessing arr[2] takes essentially the same amount of work.

So:
```
5 elements        → O(1)
1,000 elements    → O(1)
1,000,000 elements → O(1)
```

### O(n) — Linear Time

Definition:
O(n) means the amount of work performed by an algorithm increases proportionally with the input size n. If the input becomes larger, the algorithm may need to perform more operations.

Example — Searching an array:
```javascript
const arr = [10, 20, 30, 40, 50];

for (let i = 0; i < arr.length; i++) {
    if (arr[i] === 50) {
        console.log("Found");
        break;
    }
}
```
Here, we may have to check every element.
```
5 elements          → up to 5 checks
100 elements        → up to 100 checks
1,000 elements      → up to 1,000 checks
1,000,000 elements  → up to 1,000,000 checks
```
Therefore, it is O(n).

The key difference

O(1): The input size can grow, but the amount of work stays approximately constant.

O(n): As the input size grows, the amount of work grows with it.

Easy memory trick:
```
O(1) → fixed work
O(n) → work follows n
```
