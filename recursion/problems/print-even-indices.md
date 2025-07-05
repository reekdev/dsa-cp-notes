
```java
public static String solve(int[] arr) {  
    StringBuilder sb = new StringBuilder();  
    helper(arr, 0, sb);  
    return sb.toString();  
}  
  
private static void helper(int[] arr, int index, StringBuilder sb) {  
    if (index == arr.length) return;  
    helper(arr, index+1, sb);  
    if (index % 2 == 0) {  
        if (!sb.isEmpty()) sb.append(" ");  
        sb.append(arr[index]);  
    }  
}
```

