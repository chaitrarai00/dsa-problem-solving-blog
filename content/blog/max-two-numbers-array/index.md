---
title: Maximum 2 numbers in an array
date: "2021-07-22T22:40:32.169Z"
description: find 2 largest/maximum numbers in an array code
---

##The problem statement is to find 2 largest/maximum numbers in an array code

> one could sort the array and find 2nd or nth large elements from the array based on the index.

```java
 public static String fun(int a[])
    {
        int n=a.length;
        Arrays.sort(a);
        return a[n-1]+" "+a[n-2];
    }
```

_As mentioned in the official JavaDoc, Arrays.sort uses dual-pivot Quicksort on primitives. It offers O(n log(n)) performance and is typically faster than traditional (one-pivot) Quicksort implementations. However, it uses a stable, adaptive, iterative implementation of mergesort algorithm for Array of Objects._

###Time complexity of this algorithm would be O(nlogn)

> Another way is to compare the values get the largest of all and the with the largest number as reference get the next largest

> This algorithm will get a little complex and problematic with you will have to find the nth maximum numbers for large n values

```java
public static String fun(int a[])
{
    int n=a.length;
    int largest_one=0;
    int largest_two=0;
    for(int i=0;i<n;i++){
        if(a[i]>largest_one)
            largest_one=a[i];
        else if(a[i]<largest_one && largest_two<a[i])
            largest_two=a[i];
    }
    return largest_one+" "+largest_two;
}
```

###Time complexity of this algorithm would be O(n)
