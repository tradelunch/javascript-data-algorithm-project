# minimum subarray:: O(N), O(1)

{% embed url="https://www.dailycodingproblem.com/solution/852?token=657efe76657dae61b124f712d801231579562f302efbfd2192072e674bca41fd182597f4" %}
solution
{% endembed %}

```javascript
def maximum_circular_subarray(arr):
    max_subarray_sum_wraparound = sum(arr) - min_subarray_sum(arr)
    return max(max_subarray_sum(arr), max_subarray_sum_wraparound)


def max_subarray_sum(arr):
     max_ending_here = max_so_far = 0
     for x in arr:
         max_ending_here = max(x, max_ending_here + x)
         max_so_far = max(max_so_far, max_ending_here)
     return max_so_far


def min_subarray_sum(arr):
     min_ending_here = min_so_far = 0
     for x in arr:
         min_ending_here = min(x, min_ending_here + x)
         min_so_far = min(min_so_far, min_ending_here)
     return min_so_far
```



min\_subArray\_sum

연속적으로 이루어진 subArray 중 가장 작은 값을 가진 부분을 날려 버리면?

```javascript
[5, -1, -2, -5, -1, 6]

// max sub array
[5, 4, 2, -3, -1, 6]
6 이 가장 큰 sub array sum 이다
값이 0 으로 떨어지기 전에는 연속하는 current Sum 을 구해주고 
값이 0 이하로 떨어진 이후엔 
```

<figure><img src="../../../../.gitbook/assets/kadane-algorithm-tmb (1).jpg" alt=""><figcaption><p>max sub array sum</p></figcaption></figure>







```javascript
// min sub array
[0, -1, -3, -8, -9, -3] 
-9 이 의미하는 바는 [-1, -2, -5, -1] 의 합이고 이 sub array가 이 배열에서 가장 작은 합을 형성한다.

-9 가 음수이기 때문에 이 값을 total sum에서 빼면
2 - (-9) = 11 로 최대 값을 가지는 circular sub array [6] -> [5]를 구할 수 있다.


// extra
-9 가 아니라 1 이면 
2 - 1 = 1 이기 때문에 이 값이 최대 sub array 합이 아닐 수 있다.

```



```javascript
그래서 그것을 확인하기 위해

max_subarray_sum_wraparound = sum(arr) - min_subarray_sum(arr)
max(max_subarray_sum(arr), max_subarray_sum_wraparound)

max (max_subarray_sum, total - 최저 합을 나타내는 구간 sub array)
으로 마지막 변수를 체크 한다 

최저 합을 나타내는 구간 sub array => 음수일 경우 확인 용

```





