```java
public int binarySearch(int[] nums, int target) {  
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

a common technique to avoid the integer overflow while doing this

```java
var mid = (left + right) / 2
```

So you can calculate the mid like this. It is essentially the same thing.

```java
var mid = left + (right - left) / 2;
```

Also, to make the division slightly faster you can do this

```java
var mid = left + ((right - left) >> 1);
```

You could also write the algorithm using `for loop` instead of `while loop`

```java
public int binarySearch(int[] nums, int target) {  
    for (int left = 0, right = nums.length - 1; left <= right;) {  
        int mid = left + ((right - left) >> 1);  
        if (target == nums[mid]) return mid;  
        else if (target < nums[mid]) right = mid - 1;  
        else left = mid + 1;  
    }  
    return -1;  
}
```

