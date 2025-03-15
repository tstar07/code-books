# **📌 Big-O Notation Guide**  

Big-O notation helps us **measure how efficient** an algorithm is in terms of **time** and **space** as the input size grows.  

---

## **📝 Common Big-O Complexities**  

| Complexity | Name | Example | Performance |
|------------|-----------------|--------------------|--------------|
| **O(1)** | Constant Time | Accessing `arr[i]` | ✅ Fastest |
| **O(log n)** | Logarithmic Time | Binary Search | 🔥 Very Fast |
| **O(n)** | Linear Time | Looping through an array | ⚡ Good |
| **O(n log n)** | Linearithmic Time | Merge Sort, Quick Sort | 🔄 Efficient |
| **O(n²)** | Quadratic Time | Nested loops (Brute force) | 🐢 Slow |
| **O(2ⁿ)** | Exponential Time | Fibonacci (Recursive) | 🛑 Very Slow |
| **O(n!)** | Factorial Time | Traveling Salesman Problem | ❌ Worst |

---

## **🚀 Key Takeaways**  

1️⃣ **Lower complexity = Faster execution** ✅  
2️⃣ **O(1) and O(log n) are best for efficiency** 💡  
3️⃣ **O(n²), O(2ⁿ), and O(n!) should be avoided** 🚫  

---

## **Understanding Common Complexities**  

### **1️⃣ O(1) - Constant Time**  
- The execution time **does not change** with input size.  
- Takes the **same amount of time**, no matter how large the input is.  

✅ **Example: Accessing an array element by index**  
```js
let arr = [10, 20, 30, 40];
console.log(arr[2]); // Always takes the same time O(1)
```
**Reason:** No loops, just direct access.  

---

### **2️⃣ O(n) - Linear Time**  
- The time taken **grows linearly** with the input size.  
- If `n` increases, execution time increases **proportionally**.  

✅ **Example: Looping through an array**  
```js
let arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]); // Runs 'n' times → O(n)
}
```
**Reason:** If `n = 100`, the loop runs 100 times.  

---

### **3️⃣ O(n²) - Quadratic Time**  
- If the input size doubles, the execution time **increases quadratically**.  
- Usually occurs with **nested loops**.  

✅ **Example: Nested loops (pairing elements in an array)**  
```js
let arr = [1, 2, 3];
for (let i = 0; i < arr.length; i++) {
  for (let j = 0; j < arr.length; j++) {
    console.log(arr[i], arr[j]); // Runs n² times
  }
}
```
**Reason:** If `n = 3`, the loop runs `3 × 3 = 9` times.  

---

### **4️⃣ O(log n) - Logarithmic Time**  
- The input size reduces **exponentially** in each step.  
- Mostly found in **binary search**.  

✅ **Example: Binary Search**  
```js
function binarySearch(arr, target) {
  let left = 0, right = arr.length - 1;
  while (left <= right) {
    let mid = Math.floor((left + right) / 2);
    if (arr[mid] === target) return mid;
    else if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
}
```
**Reason:** We divide the problem **in half** each time, so it runs in **O(log n)**.  

---

### **5️⃣ O(n log n) - Linearithmic Time**  
- Used in **efficient sorting algorithms** like **Merge Sort & Quick Sort**.  
- Slightly worse than **O(n)** but much better than **O(n²)**.  

✅ **Example: Merge Sort**  
```js
function mergeSort(arr) {
  if (arr.length <= 1) return arr;
  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));
  return merge(left, right);
}
```
**Reason:** It splits `n` elements in half (`log n` times) and does `O(n)` work at each step.  

---

## **📌 Space Complexity (O(1) vs O(n))**  

| Complexity | Description |
|------------|------------|
| **O(1)** | Constant Space → No extra memory used, modifies input in-place |
| **O(n)** | Linear Space → Extra memory grows with `n` |

✅ **Example of O(1) Space:**  
```js
let sum = 0; // Using only a few variables → O(1)
for (let i = 0; i < n; i++) {
  sum += i;
}
```

✅ **Example of O(n) Space:**  
```js
let newArray = []; // Creating a new array → O(n)
for (let i = 0; i < n; i++) {
  newArray.push(i);
}
```

---

## **📌 Summary Table**  

| Complexity | Example | Behavior |
|------------|---------|----------|
| **O(1)** | Array indexing | Constant time |
| **O(n)** | Looping through an array | Grows linearly |
| **O(n²)** | Nested loops | Quadratic growth |
| **O(log n)** | Binary search | Reduces input size exponentially |
| **O(n log n)** | Merge Sort | Fast sorting |

---

## **🚀 Final Thoughts**  
✅ **O(1) is the fastest**, while **O(n²) or worse should be avoided** if possible.  
✅ **Binary search (`O(log n)`) is efficient** for searching in sorted data.  
✅ **Sorting (`O(n log n)`) is better than brute force (`O(n²)`)**.  

---
