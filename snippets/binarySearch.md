### binarySearch

Use recursion to perform a logarithmic search similar to `.indexOf()` that finds the index of a value within an array. The two differences being 
1. Opperation only works with sorted arrays
2. Offers a major performance boost when compared liner search or `.indexOf()` 

```js
const binarySearch = (arr, val, start = 0, end = arr.length - 1) => {
  if (start > end) return -1;
  let mid = Math.floor((start + end) / 2);
  let target = arr[mid];
  if (target > val) return binarySearch(arr, val, start, mid-1);
  if (target < val) return binarySearch(arr, val, mid+1, end);
  return mid;
}
```

```js
binarySearch([1, 4, 6, 7, 12, 13, 15, 18, 19, 20, 22, 24], 6); // 2
```
