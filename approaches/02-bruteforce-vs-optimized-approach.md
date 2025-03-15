### **Problem-Solving: Brute Force vs. Optimized Approach**  

#### **1️⃣ What is Brute Force?**  
Brute force is a straightforward way to solve a problem by checking all possible solutions without considering efficiency.  

🔹 **Example**: Find if an array contains a pair that sums up to a target value.  
- **Brute Force Approach**: Use two nested loops to check every pair.  
- **Time Complexity**: **O(n²)** (inefficient for large inputs).  

```js
function hasPairWithSumBrute(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] + arr[j] === target) {
                return true;
            }
        }
    }
    return false;
}

console.log(hasPairWithSumBrute([1, 2, 3, 4, 6], 10)); // false
console.log(hasPairWithSumBrute([1, 2, 3, 4, 6], 7)); // true
```

---

#### **2️⃣ Optimized Approach**  
Instead of checking all pairs, we use a **Hash Set** to store numbers and check if the complement exists.  

🔹 **Time Complexity**: **O(n)** (much faster).  

```js
function hasPairWithSumOptimized(arr, target) {
    const seen = new Set();
    for (let num of arr) {
        if (seen.has(target - num)) {
            return true;
        }
        seen.add(num);
    }
    return false;
}

console.log(hasPairWithSumOptimized([1, 2, 3, 4, 6], 10)); // false
console.log(hasPairWithSumOptimized([1, 2, 3, 4, 6], 7)); // true
```

---

### **Key Takeaways**
✅ Brute Force tries all possibilities (**O(n²)**).  
✅ Optimized solutions use **data structures** (Hashing, Two Pointers, etc.) to reduce time complexity.  
✅ Always analyze **time & space complexity** before choosing an approach.  
