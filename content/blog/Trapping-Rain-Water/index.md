---
title: Trapping Rainwater Problem
date: "2021-08-02T22:40:32.169Z"
description: Find maximum rainwater
---

```java
public static int fun(int a[],int n)
{
    int result=0;
    int low=0,high=n-1;
    int leftmax=0,rightmax=0;
    while(low<=high){
        if(a[low]<a[high]){
            if(a[low]>leftmax)
                leftmax=a[low];
            else
                result+=leftmax-a[low];
            low++;
        }
        else{
            if(a[high]>rightmax)
                rightmax=a[high];
            else
                result+=rightmax-a[high];
            high--;
        }
    }
        return result;
}
```

```java
public static int fun(int a[],int n)
{
    int result=0;
    int[] left=new int[n];
    int[] right=new int[n];
    left[0]=a[0];
    for(int i=1;i<n;i++){
        left[i]=Math.max(left[i-1],a[i]);
    }
    right[n-1]=a[n-1];
    for(int i=n-2;i>=0;i--){
        right[i]=Math.max(right[i+1],a[i]);
    }
    for(int i=1;i<n-1;i++){
        result+=Math.min(left[i],right[i])-a[i];
    }
    return result;
}
```
