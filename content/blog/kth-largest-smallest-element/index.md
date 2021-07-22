---
title: kth smallest or largest element
date: "2021-07-22T22:40:32.169Z"
description: The nth smallest element in an array (without using array functions)
---

##The Problem statement is to find the kth smallest element in an array

> Using arrays.sort we can get the kth smallest/largest elemnt based on indexing.

> But if we were to not use the array functions we will have to take a sort and partition selectively to select the kth largest element

> we use a helper function partition to get a quick sort of the elements

```java
public static int fun(int[] a,int low, int high, int k)
{
   if(k>0 && k<=(high-low+1)){
       int position=partition(a,low,high);
       if(position-low==k-1)
            return a[k-1];
        else if(position-low>k-1)
            return fun(a,low,position-1,k);
        else
            return fun(a,position+1,high,k);
   }
   return -1;
}

public static int partition(int[] a,int low,int high)
{
    int i=low;
    int pivot=a[high];
    for(int j=low;j<high;j++){
        if(a[j]<pivot){
            int temp=a[j];
            a[j]=a[i];
            a[i]=temp;
            i++;
        }
    }
    int temp=a[high];
    a[high]=a[i];
    a[i]=temp;
    return i;
}
```

###The time complexity O(n) on average and O(n^2 worst)
