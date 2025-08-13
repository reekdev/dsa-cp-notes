## Uppercase to Lowercase

```java
char upper = 'T';  
char lower = (char)(upper + ('a' - 'A')); // contains 't'
```

**Explanation**

`upper` holds the value `T` which is of type `char`  
In Unicode/ASCII, `T` has the code `84`


---

## Lowercase to Uppercase

```java
char lower = 't';  
char upper = (char)(lower - ('a' - 'A')); // contain 'T'
```

