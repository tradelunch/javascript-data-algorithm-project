# Subarray Sort

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 13.12.29.png>)

### Wrong

* n, 1
* This is wrong!!!! cuz from start, end does not sorted

<pre class="language-jsx"><code class="lang-jsx"><strong>~~function subarraySort(arr) {
</strong>  let min = Infinity;
  let max = -Infinity;
  
  let start = Infinity;
  for (let i = 1; i &#x3C; arr.length; i++) {
    if (arr[i - 1] &#x3C;= arr[i]) continue;
    start = i;
    min = Math.min(arr[i], min);
  }

  if (start === Infinity) return [-1, -1];

  let end = -Infinity;
  for (let i = arr.length - 2; i >= 0; i--) {
    if (arr[i] &#x3C;= arr[i + 1]) continue;
    end = i;
    max = Math.max(arr[i], max);
  }

  console.log({
    start,
    end,
    min,
    max
  });

  // 1 2 3 4 5 4
  // if (start >= end) 
  //   return [end - 1, arr.length - 1];

  // // 5 3 2 1 
  // // 1 2 3 12 5 6 7 12 5 22 24 25

  // // find lower bound
  let lower = start;
  let target = min;
  let s = -1;
  let e = start;
  while (s + 1 &#x3C; e) {
    const m = s + Math.floor( (e - s) / 2);
    if (arr[m] >= target + 1) {
      e = m;
    } else {
      s = m;
    }
  }
  lower = Math.min(e, end);
  console.log({
    lower
  });

  let upper = end;
  target = max;
  s = end;
  e = arr.length;
  while (s + 1 &#x3C; e) {
    const m = s + Math.floor( (e - s) / 2);
    if (arr[m] >= target) {
      e = m;
    } else {
      s = m;
    }
  }
  upper = Math.max(s, start);
  console.log({
    lower,
    upper
  });

  // target = arr[end];
  // s = end;
  // e = arr.length;

  

  return [lower, upper];
}

// Do not edit the line below.
exports.subarraySort = subarraySort;~~
</code></pre>

### Good

* n, 1

```jsx
function isValid(i, arr) {
  if (i === 0) return arr[i] <= arr[i + 1];
  if (i === arr.length - 1) return arr[i - 1] <= arr[i];
  return arr[i] <= arr[i + 1] && arr[i - 1] <= arr[i];  
}
function subarraySort(arr) {
  let min = Infinity;
  let max = -Infinity;
  
  for (let i = 0; i < arr.length; i++) {
    if (isValid(i, arr)) continue;
    min = Math.min(arr[i], min);
    max = Math.max(arr[i], max);
  }

  if (min === Infinity) return [-1, -1];
  
  console.log({
    min,
    max
  });

  let lower = arr.length - 1;
  let upper = 0;

  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    if (curr <= min) continue;
    lower = i;
    break;
  }

  for (let i = arr.length - 1; i >= 0; i--) {
    const curr = arr[i];
    if (curr >= max) continue;
    upper = i;
    break;
  }

  return [lower, upper];
}

// Do not edit the line below.
exports.subarraySort = subarraySort;
```
