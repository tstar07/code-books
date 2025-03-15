# Binary Search

Binary Search is an efficient algorithm used to find an element in a **sorted array**. It follows the **Divide & Conquer** approach, repeatedly dividing the search space in half.

---

## 🔹 Key Takeaways
✔ Works only on **sorted arrays**.  
✔ **Time Complexity**: O(log n) (Very Fast!)  
✔ **Space Complexity**: O(1) (Iterative) / O(log n) (Recursive)  
✔ **Divide & Conquer** approach  

---

## 🔹 Iterative Approach

```js
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid; // Target found, return index
        } else if (arr[mid] < target) {
            left = mid + 1; // Search right half
        } else {
            right = mid - 1; // Search left half
        }                
    }
    return -1; // Target not found
}

// ✅ Test Cases
console.log(binarySearch([1, 3, 5, 7, 9, 11, 15], 7));  // Output: 3
console.log(binarySearch([1, 3, 5, 7, 9, 11, 15], 10)); // Output: -1
```

### ✅ Why Iterative is Better?
✔ Uses **O(1) space** (constant space) since no extra function calls are made.  
✔ **Faster execution** as no stack memory is consumed.  
✔ Recommended for large datasets.  

---

## 🔹 Recursive Approach

```js
function binarySearchRecursive(arr, target, left = 0, right = arr.length - 1) {
    if (left > right) return -1; // Base case: Target not found

    let mid = Math.floor((left + right) / 2);

    if (arr[mid] === target) {
        return mid; // Target found, return index
    } else if (arr[mid] < target) {
        return binarySearchRecursive(arr, target, mid + 1, right); // Search right half
    } else {
        return binarySearchRecursive(arr, target, left, mid - 1); // Search left half
    }
}

// ✅ Test Cases
console.log(binarySearchRecursive([1, 3, 5, 7, 9, 11, 15], 7));  // Output: 3
console.log(binarySearchRecursive([1, 3, 5, 7, 9, 11, 15], 10)); // Output: -1
```

### ⚠️ Drawbacks of Recursion
❌ Uses **O(log n) space** due to recursive function calls (stack memory).  
❌ Might cause **stack overflow** for very large arrays.  

---

## 🔹 Binary Search Variations
- **Lower Bound Search**: Finds the first occurrence of an element.
- **Upper Bound Search**: Finds the last occurrence of an element.
- **Binary Search on Answer**: Used in problems like "Find Minimum in Rotated Sorted Array".

---

## 🔹 When to Use Binary Search?
✅ Searching for an element in a **sorted array**.  
✅ Optimizing search in problems with **monotonic behavior** (e.g., "Find the First Bad Version").  
✅ Solving **algorithmic problems** efficiently instead of brute-force searching.  

---

## 🔹 Optimizing Search in Monotonic Problems
In problems where behavior is **monotonic** (either always increasing or always decreasing), Binary Search helps optimize the search process.

### 🛠 **Example: Find the First Bad Version**
Imagine a system where versions of software are released sequentially, but at some point, a bad version is introduced. Every version after that is also bad.

📌 **Problem Statement**:
- Given `n` versions, find the first bad version.
- You have an API `isBadVersion(version)` that returns `true` if the version is bad.

### ✅ **Optimized Approach using Binary Search**
```js
function firstBadVersion(n, isBadVersion) {
    let left = 1, right = n;

    while (left < right) {
        let mid = Math.floor((left + right) / 2);
        
        if (isBadVersion(mid)) {
            right = mid; // Look on the left side
        } else {
            left = mid + 1; // Look on the right side
        }
    }
    return left; // First bad version
}
```

### 🔹 **Why Does This Work?**
- If `mid` is bad, all versions after `mid` are bad, so we **eliminate the right half**.
- If `mid` is good, the bad version must be **on the right side**.

### 🚀 **Time Complexity**
- **O(log n)** since we're halving the search space each time.
---
### 🔹 Real-World Applications of Binary Search

    - Searching in Large Databases
        Used in indexing databases (e.g., MySQL, PostgreSQL) to quickly retrieve records.

    - Autocomplete & Dictionary Search
        Used in search engines, spell checkers, and auto-suggestions to quickly find words.

    - Finding the Square Root of a Number
        Used to approximate the square root using a modified binary search approach.

    - Media & Streaming Services
        YouTube, Netflix, and Spotify use Binary Search to fast-forward and rewind to a specific timestamp efficiently.

    - Version Control (Find First Bad Version)
        Used in debugging and testing systems where a bad update needs to be located efficiently.

    - Load Balancing & System Optimization
        Applied in distributed systems to balance server loads optimally.

    - Computational Geometry
        Used in problems like finding the closest pair of points in a set of coordinates.

    - Competitive Programming & Algorithmic Problems
        Rotated Sorted Array Search, Finding Peak Element, Finding First and Last Occurrence in a Sorted Array.

---

## 🔹 Summary
| Approach  | Time Complexity | Space Complexity | Pros | Cons |
|-----------|---------------|----------------|------|------|
| **Iterative**  | O(log n)  | O(1) | Fast, uses constant space | - |
| **Recursive**  | O(log n)  | O(log n) | Easier to write | Stack overflow risk |

Binary Search is an essential technique in **competitive programming, interviews, and system optimization**. Mastering its variations will help solve **many real-world search problems efficiently!** 🚀



