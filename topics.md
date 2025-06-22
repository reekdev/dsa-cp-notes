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

Okay so my initial observation was that there is no way it can be made into a square if the sum of all the area is not a perfect square.

After I checked that i.e. the summed area *is* a perfect square, there can be two distinct cases:
1. all the lengths `(l1, l2, l3)` are equal and all the breadth `(b1, b2, b3)` equal to the length
2. all the breadth `(b1, b2, b3)` are equal and all the length `(l1, l2, l3)` equal to the breadth.

And of course, if the first rectangle is a perfect square then there is no way that adding the other two rectangles will result in a square (think about it).

After the last two checks are done (i.e. equal length and equal breadth), there is a very important observant. That is, only the first rectangle is the biggest. Other two will be smaller.

