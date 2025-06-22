```java
public int search(int[] nums, int target) {  
    var left = 0;  
    var right = nums.length - 1;  
  
    while (left <= right) {  
        var mid = (left + right) / 2;  
        if (target == nums[mid]) return mid;  
        else if (target < nums[mid]) right = mid - 1;  
        else left = mid + 1;  
    }  
    return -1;  
}
```

a common technique to avoid the integer overflow in `(left + right) / 2` is this 