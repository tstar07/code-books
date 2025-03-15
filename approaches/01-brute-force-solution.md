### **What is a Brute-Force Solution?**  
A **brute-force solution** is the **most straightforward** way to solve a problem, even if it’s not the most efficient. It usually involves trying **all possible cases** and using **nested loops** or extra computation.  

#### **For our problem (Product of Array Except Self):**  
A brute-force approach would be:  
- Loop through the array.  
- For each index, calculate the product of all other elements by using another loop.  
- Store the results in a new array.  

#### **Brute-Force Code:**
```js
function productExceptSelf(nums) {
  let n = nums.length;
  let result = new Array(n).fill(1);

  for (let i = 0; i < n; i++) { // Pick each element
    let product = 1;
    for (let j = 0; j < n; j++) { // Multiply all except itself
      if (i !== j) {
        product *= nums[j];
      }
    }
    result[i] = product;
  }

  return result;
}

console.log(productExceptSelf([1, 2, 3, 4])); // Output: [24, 12, 8, 6]
```
### **Why is it Brute-Force?**
- We are using **two loops**, so the **time complexity is O(n²)** (slow for large inputs).  
- It works but is **not efficient**.  

