---
title: Bridge and Torch Problem
date: "2021-08-02T22:40:32.169Z"
description: Find minimum time for crossing the bridge
---
##Given an array of positive distinct integer denoting the crossing time of ‘n’ people. These ‘n’ people are standing at one side of bridge. Bridge can hold at max two people at a time. When two people cross the bridge, they should have a light torch at all times. There is only one light torch. Find the minimum total time in which all persons can cross the bridge.

>given array: {1,2,50,75,100,150,200}

>two people would have to 
>
>

```java
public static int fun(int a[],int n)
{
    int result=0;
    if(n<3){
        result=a[n-1];
    }
    else if(n==3){
        result=a[0]+a[1]+a[2];
    }
    else{
        result+=a[1]+a[0]+a[n-1]+a[1]+fun(a,n-2);
    }
    return result;
}
```