---
title: Missing number in an array
date: "2021-07-19T22:40:32.169Z"
description: The problem statement is to find the missing number in a given input array
---

##find the missing number in a given input array:[1,2,3,5,6,7] should give 4

> As seen the array would always be one value above the next element in the series

> So the values can be compared to the next element in the array

> Every element at index i is compared with the element at index i+1

> if they are equal you proceed else the value missing at index i+1 would be a[i]+1

```java
 public static int fun(int a[])
  {
    for(int i=0;i<a.length;i++){
		if(a[i]+1!= a[i+1])
			return a[i]+1;
	    }
	    return -1;
   }
```

##Every element has to be compared with the element next to it. The time would be increasing with n, where n is size of array so time complexity would be O(n)

> One can try to use the sum formula: s=n\*n+1/2 which would be the actual sum

> This formula applies assuming the array starts from 1,2..n

> then subtract the actual sum with the sum obtained from elements in given array

```java
 public static int fun(int a[])
  {
    int n=a[a.length-1];
    int actual_sum=(n*(n+1))/2;
    int sum=0;
    for(int i=0;i<a.length;i++){
        sum+=a[i];
	  }
	  return actual_sum-sum;
  }
```

##Time complexity would be O(n)

> If the input array goes like {5,6,8,9} its does not start from 1 so the formula above wont apply

> assuming that there is exactly one value missing hence the total length of actaul array would be length of given array +1

> we can try to get the missing value using another formula n\*(f+l)/2 where f is the first element in the array and l is the last elemnt in the array

```java
 public static int fun(int a[])
  {
    int f=a[0];
    int l=a[a.length-1];
    int actual_sum=(a.length+1)*(f+l)/2;
    int sum=0;
    for(int i=0;i<a.length;i++){
		  sum+=a[i];
	  }
	  return actual_sum-sum;
    }
```

##Time complexity would be O(n)
