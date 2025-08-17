[link](https://www.geeksforgeeks.org/problems/subarray-with-given-sum-1587115621/1#-hashing-prefix-sum-ontime-and-on-space)


```java
class Solution {
    static ArrayList<Integer> subarraySum(int[] arr, int target) {
        int n = arr.length;
        ArrayList<Integer> list = new ArrayList<>();
        long sum = 0L;
        for (int start = 0, end = 0; start < n && end < n;) {
            sum += arr[end];

            /**
             * Keep adding as long as the sum is less than target.
             * This step tries to find a candidate window.
             **/
            if (sum < target) {
                ++end; continue;
            }

            /**
             * If the sum is greater than or equal to the target
             * that means you have a candidate window (sub-array)
             **/
            if (sum >= target) {
                /**
                 * As long as the sum of candidate window is
                 * greater than the target, I need to shrink the window
                 * from the beginning in order to bring the sum closer to target.
                 **/
                for (; sum > target ;) sum -= arr[start++];

                if (sum == target) {
                    list.addAll(List.of(start+1, end+1));
                    break;
                }

                /**
                 * While I was decreasing the window from beginning,
                 * I may have made the sum lesser than target,
                 * In which case I need to increment my end pointer.
                 **/
                if (sum < target) ++end;
            }
        }
        if (list.isEmpty()) return new ArrayList<Integer>(List.of(-1));
        return list;
    }
}
```