---
title: Largest Sum Contiguous Subarray
date: "2021-07-23T22:40:32.169Z"
description: Find the Largest Sum in the given array which is a Contiguous Subarray
---

##Problem statement is to Find the Largest Sum in the given array which is a Contiguous Subarray

> We will keep a maximum_result to store the maximum sum value

> while iterating there could be times when the sum that is maximum is encountered in the beginning or at the end

> to remember and store the sum and preserve the actual result we take another temporory variable to store the sum that we get while iterating through each element

> This algorithm is also called the Kadanes Algorithm

```java
public static int maximum_sum_array(int[] a)
{
  int maximum_sum_result=0;
  int maximum_sum_temp=0;
  for(int i=0;i<a.length;i++){
      maximum_sum_temp=maximum_sum_temp+a[i];
      if(maximum_sum_temp<0)
        maximum_sum_temp=0;
      else if(maximum_sum_temp>maximum_sum_result)
        maximum_sum_result=maximum_sum_temp;
  }
  return maximum_sum_result;
}
```

##Time Complexity is O(n) and O(1) extra space
