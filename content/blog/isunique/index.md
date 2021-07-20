---
title: All Unique in a String
date: "2021-07-20T22:40:32.169Z"
description: The problem statement is to implement an algorithm to determine if a string has all unique characters.
---

##implement an algorithm to determine if a string has all unique characters. Try by using a datastructure and witout using a datastructor

> check is the character at index i is equal to character at index i+1

> return false if the values are equal else true

```java
public static boolean fun(String str)
    {
        for(int i=0;i<str.length()-1;i++){
            if(str.charAt(i)==str.charAt(i+1))
                return false;
        }
        return true;
    }
```
