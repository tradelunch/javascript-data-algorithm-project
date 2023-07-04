# Union Find

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 19.51.32.png>)

#### Calculate time complexity

* nothing ⇒ n
* set up & update weights for each root ⇒ logn
* **Ackerman ⇒ ɑ(n)**

#### Applied to Disjoint-set forests

from [Wikipedia](http://en.wikipedia.org/wiki/Disjoint-set\_data\_structure)

> (about find and union) These two techniques complement each other; applied together, the amortized time per operation is only O(α(n)), where α(n) is the inverse of the function f(n) = A(n,n), and A is the extremely quickly-growing Ackermann function. Since α(n) is the inverse of this function, α(n) is less than 5 for all remotely practical values of n. Thus, the amortized running time per operation is effectively a small constant.

```jsx
// Do not edit the class below except for
// the constructor and the createSet, find,
// and union methods. Feel free to add new
// properties and methods to the class.
class UnionFind {
  constructor() {
    // Write your code here.
    this.arr = [];
    this.weights = [];
  }

  createSet(value) {
    this.arr[value] = value;
    this.weights[value] = 0;
    return null;
  }

  // find(value) {
  //   let currentValue = value;
  //   while (this.arr[currentValue] !== undefined) {
  //     if (this.arr[currentValue] === currentValue) {
  //       return currentValue;
  //     }
      
  //     currentValue = this.arr[currentValue];
  //   }

  //   return null;
  // }

  find(value) {
    if (value === undefined) 
      return null;

    if (this.arr[value] === value)
      return value;
    

    return this.arr[value] = this.find(this.arr[value]);
  }

  union(valueOne, valueTwo) {
    // Write your code here.
    const root1 = this.find(valueOne);
    const root2 = this.find(valueTwo);

    if (root1 === root2) return null;
    if (root1 === null || root2 === null) return null;

    // this.arr[root1] = root2;

    console.log(
      {
        root1,
        root2,
      }
    )
    

		/ using weights
    const weight1 = this.weights[root1];
    const weight2 = this.weights[root2];

    if (weight1 >= weight2) {
      this.arr[root1] = root2;
    } else {
      this.arr[root2] = root1;
    }

    
    
    return null;
  }
}

// Do not edit the line below.
exports.UnionFind = UnionFind;
```
