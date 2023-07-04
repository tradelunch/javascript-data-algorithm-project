# Task Assignment - use two pointer

![](<../../../.gitbook/assets/Screenshot 2023-01-24 at 1.33.46.png>)

* nlogn, n

```jsx
function taskAssignment(k, tasks) {

  const mapped = tasks.map((t, idx) => [t, idx]).sort((a, b) => a[0] - b[0]);

  const answer = [];
  // first try
  // for (let i = 0; i <= mapped.length / 2 - 1; i++) {
  //   answer.push([mapped[i][1], mapped[mapped.length - 1 - i][1]]);
  // }

  // second try
  let idx = 0;
  let s = 0;
  let e = tasks.length - 1;
  while (idx < k) {
    const pair = [mapped[s][1], mapped[e][1]];
    answer.push(pair);
    s++;
    e--;
    idx++;
  }
  
  
  return answer;
}
// [1, 1, 3, 3, 4, 5]

// Do not edit the line below.
exports.taskAssignment = taskAssignment;
```
