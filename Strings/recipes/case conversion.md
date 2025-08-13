## Uppercase to Lowercase

```java
char upper = 'T';  
char lower = (char)(upper + ('a' - 'A')); // contains 't'
```

**Explanation**

`upper` holds the value `T` which is of type `char`  
In Unicode/ASCII, `T` has the code `84`

In Unicode/ASCII, `A` has the value `65` and `a` has the value `97`.  
The difference between the two is `32`.  
Since, this difference does not change you can just use this offset to convert cases.

So,  
when you need to convert a character to lowercase from uppercase you can add this offset 

when you need to convert a character to lowercase from uppercase you can subtrac this offset 


---

## Lowercase to Uppercase

```java
char lower = 't';  
char upper = (char)(lower - ('a' - 'A')); // contain 'T'
```

