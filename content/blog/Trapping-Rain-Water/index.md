---
title: Trapping Rainwater Problem
date: "2021-08-02T22:40:32.169Z"
description: Find maximum rainwater
---

##Given n non-negative integers representing an elevation map where the width of each bar is 1 , compute how much water it can trap after raining.

_Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6_

> The water is store when there is a dump structure to accumulate the water

> The left and right platform should be more than the current platform

> this way the water is blocked

> store a left array from particular point storing maximum value from a point to its left and a right array from particular point storing maximum value from a point to its right.

> After getting the values populated the minimum among the two arrays are subtracted from the current value

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

###Time complexity is O(n), 3 for loops corresponding to 3n times of iteration and O(n) space complexity for left and right array storage

> We can try to resuce the space complexity by avoiding the left and right array

> keep two pointers for the low and highest(or left and right)

> when low(left)< high(right) then update the maximum in left

> when high(right)>low(left) then update the maximum for right

```java
public static int fun(int a[],int n)
{
    int result=0;
    int low=0;
    int high=n-1;
    int leftmax=0
    int rightmax=0;
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

###Time Complexity is O(n) with O(1 space complexity)
