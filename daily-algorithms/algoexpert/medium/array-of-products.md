# Array of Products

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 20.03.45.png>)

* N, N

```jsx
function arrayOfProducts(arr) {
  const products = new Array(arr.length).fill(1);

  for (let i = 1; i < arr.length; i++) {
    products[i] = products[i - 1];
    products[i] *= arr[i - 1];
  }

  let runningProduct = 1;
  for (let i = arr.length - 1; i >= 0; --i) {
    products[i] *= runningProduct;
    runningProduct *= arr[i];
  }

  return products;
}

// Do not edit the line below.
exports.arrayOfProducts = arrayOfProducts;
```
