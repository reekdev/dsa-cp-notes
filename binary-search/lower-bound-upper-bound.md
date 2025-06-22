You have a zero-indexed array $A$ of length $n$ that is in **non-decreasing** order:  
$$A[0] \le A[1] \le A[2] \le \quad ... \quad \le A[n-1]$$
Now you are given a target 

## Lower bound  

**Definition:** The first (smallest) index $i$ where the value $A[i]$ is greater than or equal to `target` i.e. $A[i] \ge \text{target}$. If no such element if found then simply return the array length.

**Example:**  
```
arr = [2, 5, 6, 6, 7, 7, 7, 8, 9, 10, 11, 11]
target = 7
```