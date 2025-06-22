**Modular arithmetic**

**Combinatorics**
PnC  
Inclusion Exclusion principle  
Derangement  


**Number Theory**
GCD, LCM  
factorization techniques  
prime check
sieve of erat
segmented sieve
fast factorization


---

5 3 5 1 5 1

2 3 1 2 1 1

Okay so my initial observation was that there is no way it can be made into a square if the sum of all the area is not a perfect square.

After I checked that i.e. the summed area *is* a perfect square, there can be two distinct cases:
1. all the lengths `(l1, l2, l3)` are equal and the sum of all the breadth `(b1, b2, b3)` equal to the length
2. all the breadth `(b1, b2, b3)` are equal and the sum of all the length `(l1, l2, l3)` equal to the breadth.

And of course, if the first rectangle is a perfect square then there is no way that adding the other two rectangles will result in a square (think about it).

After the last two checks are done (i.e. equal length and equal breadth), there is a very important observant. That is, only the first rectangle is the biggest. Other two will be smaller.

Another thing is that, after the first rectangle is filled up there is a specific remaining area that needs to be filled up. For example, in the test case `2 3 1 2 1 1` the summed area is 9. After the biggest (first) rectangle is placed, there is a remaining area of `9 - (2.3) = 3`  
Now this area has to be filled up from the side where there is deficit i.e. 2 in this case.
The two length of the other two rectangle `(l2, l3)`  *has to be* equal and the sum of their breadths  `(b2+b3)` *has to be* equal to `b1`

Now, I will try to draw up the inverse of this situation by using an example that I made up. Let's say the values are `5 3 4 2 1 2`  
Summed up area is 25  
after first rectangle is filled up the remaining area is 10
it is deficit from the breadth side, so we need to try to fill up the space from that side. Need to check for whether the two breadth of the other two rectangle `(b2, b3)` are equal and whether the sum of their lengths `(l2+l3)` is equal to `l1`

Here is my code for reference, in Java:
```java
class Solver {
    public static String solve(int l1, int b1, int l2, int b2, int l3, int b3) {
        var totalArea = (l1*b1)+(l2*b2)+(l3*b3);
        var sideLength = (int) Math.sqrt(totalArea);
        if (sideLength*sideLength != totalArea) return "NO";
 
        if (((l1==l2) && (l2==l3)) && (b1+b2+b3)==sideLength) {
            return "YES";
        }
 
        if (((b1==b2) && (b2==b3)) && (l1+l2+l3)==sideLength) {
            return "YES";
        }
        if (l1==b1) return "NO";
        if (l1>b1) {
            if (b2==b3 && (l2+l3)==l1) return "YES";
            else return "NO";
        }
 
        else {
            if (l2==l3 && (b2+b3)==b1) return "YES";
            else return "NO";
        }
    }
}
```

