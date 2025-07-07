The **Recursive Leap of Faith** is a problem solving framework where you *assume* that your recursive function already works correctly for sub-problems i.e. smaller inputs, and you focus on using that assumption to solve the *current* (target) problem. This approach enables you to design elegant solutions. 

This assumption allows you to focus on two critical components:  
1. **Base case:** the *simplest* scenario where the solution is so trivial that we can directly get the answer without any computation.
2. **Recursive case:** how to break down the current problem using our "already working" function.

## The core methodology:  


## Problems:  
---

**Problem: Given a N, print from 1 to N**

Here, the simplest thing you can do is literally print the numbers.

```java
public class Main {  
    public static void main(String[] args) {  
        print(5);
    }
    
    public static void print(int n) {  
        if (n == 0) return;  
        print(n-1);  
        System.out.print(n + " ");  
    }
}
```

```
1 2 3 4 5
```

While this technically works, this is not really how you would want to do it because more complex problems won't ask you to "print" something, instead they would ask you to "return" something or "build" something.  
In a real-world setting, problems usually require you to **return a result** (such as a list or a string) rather than just print the values directly. Printing is a side effect that does not allow you to use the result anywhere else in your code. So, it is important to **build and return** the result recursively.

If we modify the problem to  
**Problem: Given a N, return a string containing numbers from 1 to N (with space)**

Now, simply printing will not do. Here, we need to return a string that looks like this  
`1 2 3 4 5 ...`

which means, the signature of the function would look like this

```
static String print(int n) {}
```

This signature says that, "Given an integer n, I will print all the numbers starting from 1 to n".

Here, the recursive leap of faith will help. Suppose your function is called with argument 5. Now assume that your function already works for argument.

which means,  
print(4) :  already returns you a string like this `1 2 3 4`  

You just need to recognize how to use this result. If you simply append a `5` after this result then your work is done.

Figure out the base case. If your function is called with the argument 1 then this problem is so trivial that you do not need to do anything, just simply returning 1 would be enough.

```java
public class Main {  
    public static void main(String[] args) {  
        var ans = print(5);  
        System.out.println(ans);  
    }  
  
    public static String print(int n) {  
        if (n == 1) return "1";
        return print(n-1) + " " + n;
    }
}
```

This approach is okay, but creating a string on every call stack is expensive. Each string concatenation (+) operation creates many intermediate strings.  So one pattern is that we create a *helper* utility function and some mutable data structure (list, set, string builder etc.). The helper takes the data structure, and performs some operation on it.

```java
public class Main {  
    public static void main(String[] args) {  
        var ans = print(5);  
        System.out.println(ans);  
    }  
  
    public static String print(int n) {  
        StringBuilder sb = new StringBuilder();  
        helper(n, sb);  
        return sb.toString();  
    }  
  
    private static void helper(int n, StringBuilder sb) {  
        if (n == 1) {  
            sb.append("1");  
            return;  
        }  
        helper(n-1, sb);  
  
        // at this point, sb already contains the previous (n-1) numbers in it.  
        sb.append(" ").append(n);  
    }
}
```

following up on this idea, there is variation of this called **tail-recursive** (or, **accumulator-style**) version of this function.

This involves:
1. carrying along an accumulator. 
2. using tail recursion style i.e. the recursive call is the last action of the function.

Why is it (arguably) better?  
it builds output **as it recurses**, rather than during the unwinding phase. the work happens during the recursion itself. It can be easily transformed into a loop. 

```java
public class Main {  
    public static void main(String[] args) {  
        var ans = print(5);  
        System.out.println(ans);  
    }  
  
    public static String print(int n) {  
        StringBuilder sb = new StringBuilder();  
        return build(1, n, sb).toString();  
    }  
  
    private static StringBuilder build(int current, int end, StringBuilder acc) {  
        if (current > end) return acc;  
  
        if (current > 1) acc.append(" ");  
        acc.append(current);  
  
        return build(current + 1, end, acc);  
    }
}
```

