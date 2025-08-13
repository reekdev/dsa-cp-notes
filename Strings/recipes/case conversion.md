## Uppercase to Lowercase

```java
char upper = 'T';  
char lower = (char)(upper + ('a' - 'A')); // contains 't'
```


---

## Lowercase to Uppercase

```java
char lower = 't';  
char upper = (char)(lower - ('a' - 'A')); // contain 'T'
```


---

**Explanation**

In Unicode/ASCII, `A` has the value `65` and `a` has the value `97`.  
The difference between the two is `32`.  
Since, this difference does not change you can just use this offset to convert cases.

So,  
when you need to convert a character to **lowercase from uppercase** you can **add** this offset.  

when you need to convert a character to **uppercase from lowercase** you can **subtract** this offset.
