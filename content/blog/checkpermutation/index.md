---
title: String Permutation
date: "2021-07-20T22:40:32.169Z"
description: The problem statement is to find if one string is the permutation of other
---

##Given two strings, write a method to decide if one is a permutation of the other

> Sort the two strings given and then compare the sorted string array

> when sorted the order would be the same in both the string and whike comparng you can check if the string values are same or not

```java
public static boolean fun(String str1,String str2)
{
    if(str1.length()!=str2.length()){
        return false;
    }
    char[] str1_array=str1.toCharArray();
    char[] str2_array=str2.toCharArray();
    Arrays.sort(str1_array);
    Arrays.sort(str2_array);
    for(int i=0;i<str1.length();i++){
        if(str1_array[i]!=str2_array[i])
            return false;
    }
    return true;
}
```

#It would take O(nLogn) time to sort and n times to thrugh the strings which gets to n+nlogn time complexity: O(nlogn)

> The maximum number of characters that can be represented in extended ASCII is 256

> we could use a count array assuming there are only 256 characters

> we take increment count array value while we iterate through first string based on character occurance

> we take decrement count array value while we iterate through second string based on character occurance

> if the count array values are 0 on checking the 2 string are permutaion of each other

> any other way the strings are not permutations of each other

```java
public static int NO_OF_CHARS=256;
public static boolean fun(String str1,String str2)
{
    if(str1.length()!=str2.length()){
        return false;
    }
    int[] count=new int[NO_OF_CHARS];
    for(int i=0;i<str1.length();i++)
    {
        count[str1.charAt(i)]++;
        count[str2.charAt(i)]--;
    }
    for(int i=0;i<str1.length();i++)
    {
        if(count[str1.charAt(i)]!=0)
            return false;
    }
    return true;
}
```

_Time complexity would be O(n)+O(n) hence O(n) and constant space of 256 count array_
