---
title: Reverse String with Spaces Preserved
date: "2021-07-21T22:40:32.169Z"
description: The problem statement is to reverse a given string without moving the spaces from its original position
---

##Given a String, reverse the given string without moving the spaces from its original position

> String is immutable so change it to charArray for processing

> take a two pointer approach a start(at 0 initially) and an end(till the end of array the length-1)

> if the encountered char is an empty space you decrement or increment the pointer based on the direction of it being the start or end

> if the encountered character is not an empty space you swap characters at start and end pointers to get a reverse.

```java
public static String fun(String str)
{
    char[] str_array=str.toCharArray();
    int start=0,end=str.length()-1;
    while(start<end){
        if(str_array[start]==' ')
            start++;
        else if(str_array[end]==' ')
            end--;
        else{
            char temp=str_array[start];
            str_array[start]=str_array[end];
            str_array[end]=temp;
            start++;
            end--;
        }
    }
    return String.valueOf(str_array);
}
```

#Time Complexity of the algorithm is O(n) and space complexity of the extra character array O(n). We cant eliminate the usage of character array as String is immutable
