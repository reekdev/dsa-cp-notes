[link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1?page=1&category=sliding-window&difficulty=Basic,Easy&sortBy=submissions)

one way is to write the code like this

```java
class Solution {
    public static int smallestSubWithSum(int x, int[] arr) {
        int currentSumInThisWindow = 0;
        int minimumWindowLength = Integer.MAX_VALUE;
        for (int left = 0, right = 0; right < arr.length; ++right) {
            currentSumInThisWindow += arr[right];

            for (; currentSumInThisWindow > x; ) {
                int currentWindowLength = right - left + 1;
                minimumWindowLength = Math.min(minimumWindowLength, currentWindowLength);
                currentSumInThisWindow -= arr[left++];
            }
        }

        return minimumWindowLength == Integer.MAX_VALUE ? 0 : minimumWindowLength;
    }
}
```

another way:

```java
class Solution {
    public static int smallestSubWithSum(int x, int[] arr) {
    	int currentSumInThisWindow = 0;
    	int minimumWindowLength = Integer.MAX_VALUE;
    	for (int left = 0, right = 0; right < arr.length; ) {
            for (; currentSumInThisWindow <= x && right < arr.length; ) {
                currentSumInThisWindow += arr[right++];
            }
            for (; currentSumInThisWindow > x && left < arr.length; ) {
                if (right - left < minimumWindowLength) minimumWindowLength = right - left;
                currentSumInThisWindow -= arr[left++];
            }
    	}
        return minimumWindowLength == Integer.MAX_VALUE ? 0 : minimumWindowLength;
    }   
}
```