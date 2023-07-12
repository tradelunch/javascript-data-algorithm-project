# Counting Sort

{% embed url="https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=zenix4078&logNo=10459405" %}

{% embed url="https://stackoverflow.com/questions/41324974/how-can-i-implement-a-countingsort-that-works-with-negative-numbers" %}



### Counting sort

```tsx
const MAX_NUM = 10000;
const MAX_SIZE = 10000;
function countingSort(numbers) {
	let maxNum = -Infinity;
	for (const n of numbers) {
		if (n <= maxNum) continue;
		maxNum = n;
	}

	// counts each number in numbers
	const counts = new Array(maxNum + 1).fill(0);
	for (const n of numbers) {
		counts[n] += 1;
	}

	// find each last index + 1 of each number
	const cumulatedCountSum = new Array(maxNum + 1).fill(0);
	cumulatedCountSum[0] = counts[0];
	for (let i = 1; i < maxNum + 1; i++) {
		cumulatedCountSum[i] = cumulatedCountSum[i - 1] + counts[i];
	}

	// sort 
	const answer = new Array(numbers.length);

	for (let i = 0; i < numbers.length; i++) {
		const n = numbers[i];
		const countedIndex = cumulatedCountSum[n];
		answer[countedIndex - 1] = n; // actual index = countedIndex - 1
		cumulatedCountSum[n] -= 1;
	}

	return answer;
}

countingSort([5, 5, 5, 3, 3, 1, 1, 0, 0]);
```

```tsx
// output
{
  numbers: [
    5, 5, 5, 3, 3,
    1, 1, 0, 0
  ],
  counts: [ 2, 2, 0, 2, 0, 3 ],
  cumulatedCountSum: [ 2, 4, 4, 6, 6, 9 ],
}

// anwer
{
	answer: [
    0, 0, 1, 1, 3,
    3, 5, 5, 5
  ],
}
```

* suffix array (N^2LogN ⇒ NLogN)

#### When Quick sort? better? When Counting sort? better?

* Range of elements is more distributed uniformly
* When time is important than space

