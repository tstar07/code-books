The **Left-Right Approach** (also called the **Prefix-Suffix Approach**) follows this pattern:  

1️⃣ **Left Pass → Accumulate values using an operator (`+`, `*`, `max`, `min`, etc.)**  
2️⃣ **Right Pass → Combine results using the same operator**  

✔ **It works with any operator!**  
- Addition (`+`) → Prefix sum  
- Multiplication (`*`) → Prefix product  
- Maximum (`max`) → Prefix max  
- Minimum (`min`) → Prefix min  

---

### **🔹 Left-Right Approach General Form**
```js
let result = new Array(n).fill(initial_value);

let left = initial_value;
for (let i = 0; i < n; i++) {
    result[i] = left;
    left = OPERATION(left, nums[i]);  // Apply operation
}

let right = initial_value;
for (let i = n - 1; i >= 0; i--) {
    result[i] = OPERATION(result[i], right);
    right = OPERATION(right, nums[i]); // Apply operation
}
```
👉 **Just replace `OPERATION` with `+`, `*`, `max`, `min`, etc.**  

---

### **📌 Example 1: Left-Right Addition (Prefix Sum)**
```js
function sumExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(0);

  let left = 0;
  for (let i = 0; i < n; i++) {
    result[i] = left;
    left += nums[i];  // Addition operation
  }

  let right = 0;
  for (let i = n - 1; i >= 0; i--) {
    result[i] += right;
    right += nums[i];  // Addition operation
  }

  return result;
}

console.log(sumExceptSelf([2, 3, 4, 5])); // Output: [12, 10, 7, 5]
```

---

### **📌 Example 2: Left-Right Multiplication (Prefix Product)**
```js
function productExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(1);

  let left = 1;
  for (let i = 0; i < n; i++) {
    result[i] = left;
    left *= nums[i];  // Multiplication operation
  }

  let right = 1;
  for (let i = n - 1; i >= 0; i--) {
    result[i] *= right;
    right *= nums[i];  // Multiplication operation
  }

  return result;
}

console.log(productExceptSelf([2, 3, 4, 5])); // Output: [60, 40, 30, 24]
```

---

### **📌 Example 3: Left-Right Maximum (Prefix Max)**
```js
function maxExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(-Infinity);

  let left = -Infinity;
  for (let i = 0; i < n; i++) {
    result[i] = left;
    left = Math.max(left, nums[i]);  // Max operation
  }

  let right = -Infinity;
  for (let i = n - 1; i >= 0; i--) {
    result[i] = Math.max(result[i], right);
    right = Math.max(right, nums[i]);  // Max operation
  }

  return result;
}

console.log(maxExceptSelf([2, 3, 4, 5])); // Output: [5, 5, 5, 4]
```

---

### **🔹 Summary**
✔ **Left-Right Approach is operator-agnostic.**  
✔ **Works with any associative operation (`+`, `*`, `max`, `min`, etc.).**  
✔ **Optimized from O(n²) (brute force) → O(n) with two passes.**  

Whenever you see a problem where an **element’s value depends on left & right elements**, think of this pattern! 🚀
---

### **🔹 Left-Right Approach Simplified**  

Imagine we have an array:  
```js
nums = [2, 3, 4, 5]
```
We want to replace each element with the **sum of all other elements** (without using the element itself).  

#### **Step 1: Left Pass**
We go **left to right**, keeping track of the sum of all previous elements.  

| Index | `nums[i]` | `left` (Sum of left elements) | `result[i]` (Store left sum) |
|--------|---------|----------------|---------------|
| 0      | 2       | 0              | 0             |
| 1      | 3       | 2              | 2             |
| 2      | 4       | 2+3 = 5        | 5             |
| 3      | 5       | 2+3+4 = 9      | 9             |

Intermediate result after **Left Pass**:  
```js
result = [0, 2, 5, 9]
```

#### **Step 2: Right Pass**
Now we go **right to left**, keeping track of the sum of all next elements.  

| Index | `nums[i]` | `right` (Sum of right elements) | `result[i]` (Update by adding right sum) |
|--------|---------|----------------|---------------|
| 3      | 5       | 0              | 9+0 = 9       |
| 2      | 4       | 5              | 5+5 = 10      |
| 1      | 3       | 4+5 = 9        | 2+9 = 11      |
| 0      | 2       | 3+4+5 = 12     | 0+12 = 12     |

Final result after **Right Pass**:  
```js
result = [12, 10, 7, 5]
```
Each index now holds the sum of all other elements! ✅  

---

### **🔹 Code Implementation**
```js
function sumExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(0);

  let left = 0;
  for (let i = 0; i < n; i++) {
    result[i] = left;
    left += nums[i];  // Add current element to left sum
  }

  let right = 0;
  for (let i = n - 1; i >= 0; i--) {
    result[i] += right;
    right += nums[i];  // Add current element to right sum
  }

  return result;
}

console.log(sumExceptSelf([2, 3, 4, 5])); // Output: [12, 10, 7, 5]
```

---

### **🔹 Key Idea**
- **Left Pass:** Build up the left-side contribution.  
- **Right Pass:** Multiply/add/update with the right-side contribution.  
- **Final array contains the desired result in O(n) time.**  

Yes! **Left-Right Approach** is a common **prefix-suffix** technique used in many problems. The idea is:  

1️⃣ **Left Pass → Accumulate results from the left**  
2️⃣ **Right Pass → Multiply (or add/subtract) with results from the right**  

This approach works for **sum, product, min/max values, and even prefix sums in subarrays**.  

---

### **📌 When to Use Left-Right Approach?**
- When an element’s value **depends on elements before & after** it.  
- When **avoiding nested loops (O(n²))** by using two O(n) passes.  
- When **division isn’t allowed**, but you need **prefix & suffix values**.

---

## **🔹 Example: Left-Right Sum Array**
Instead of the **product**, let’s find the **sum of all other elements** at each index.

```js
function sumExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(0);

  let leftSum = 0;
  for (let i = 0; i < n; i++) {
    result[i] = leftSum;
    leftSum += nums[i];  // Update left sum
  }

  let rightSum = 0;
  for (let i = n - 1; i >= 0; i--) {
    result[i] += rightSum;
    rightSum += nums[i]; // Update right sum
  }

  return result;
}

console.log(sumExceptSelf([2, 3, 4, 5])); // Output: [12, 10, 7, 5]
```
**🟢 Explanation:**  
- **Left Pass stores sum of elements before index**  
- **Right Pass adds sum of elements after index**  
- **Final array contains sum except self**  

✅ Works just like the **productExceptSelf**, but with **addition** instead of multiplication.  

---

## **🔹 Another Example: Left-Right Maximum**
Find the **maximum of all elements except the current index**.

```js
function maxExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(-Infinity);

  let leftMax = -Infinity;
  for (let i = 0; i < n; i++) {
    result[i] = leftMax;
    leftMax = Math.max(leftMax, nums[i]);
  }

  let rightMax = -Infinity;
  for (let i = n - 1; i >= 0; i--) {
    result[i] = Math.max(result[i], rightMax);
    rightMax = Math.max(rightMax, nums[i]);
  }

  return result;
}

console.log(maxExceptSelf([2, 3, 4, 5])); // Output: [5, 5, 5, 4]
```
✅ **Idea is the same!**  
- **Left pass stores max before index**  
- **Right pass updates max after index**  

---

## **🔹 Conclusion**
For **sum, product, min, max, etc.**, the **left-right approach** helps:  
✔ Reduce nested loops (**O(n²) → O(n) complexity**)  
✔ Avoid using extra space (**O(1) auxiliary space**)  
✔ Simplify prefix & suffix-based problems  