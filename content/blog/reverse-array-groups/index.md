---
title: Reverse Array in given Groups
date: "2021-07-18T22:40:32.169Z"
description: The problem statement is to reverse a given array based on groups of size k
---

##Say you have an array {1,2,3,4,5,6,7,8} and you are given a value k=3 which is the group value. Your task is to reverse this array per k groups i.e, for this input output would be {3,2,1,6,5,4,8,7}

> iterate throught the array and swap with left and right

> use a sliding technique by updating left and right values for each k window

> left being i,i+k,i+2k...n-1

> right being i+k-1...n-1 for every i

> special case to consider if the given k is not a multiple of size of a then make sure to avoid array out of bounds by comparing the last value and new right value.

```java
public static int[] fun(int a[],int k)
{
  int n=a.length;
  for(int i=0;i<n;i+=k){
      int left=i;
      //Math.min is taken to consider the special case of k not being a multiple
      int right=Math.min(i+k-1,n-1);
      int temp;
      while(left<right){
        temp=a[left];
        a[left]=a[right];
        a[right]=temp;
        left+=1;
        right-=1;
      }
   }
  return a;
}
```

_Time complexity would be O(n) where each element is changed from its position once_
