---
title: based on arrival and departure time decide how many platforms are needed
date: "2021-07-22T22:40:32.169Z"
description: find no of platforms needed based on arrival and departure time decide
---

##The problem statement is to find the number of platforms that are needed based on arrival and departure time given (eg: arrival:{9.00,9.40,9.50,11.00,15.00,18.00}departure:{9.10,12.00,11.20,11.30,19.00,20.00};)

> The platform has to be increased to make space for new arrival: when the arrival time of next vehicle is greater than the departure time of the previous vehicle.

> The platforms can be decreased when the new arrival is less than the departure. The vehicle can be parked in exsisting platform

> platforms variable is changing based on conditions given so a result vairable is taken to keep the value in check for each i and j

```java
public static int fun(double[] arr,double[] dep)
{
    Arrays.sort(arr);
    Arrays.sort(dep);
    int n=arr.length;
    int platforms=1;
    int result=1;
    int i=1,j=0;
    while(i<n && j<n){
        if(arr[i]<dep[j]){
            platforms++;
            i++;
        }
        else if(arr[i]>dep[j]){
            platforms--;
            j++;
        }
        if(result<platforms)
            result=platforms;
    }
    return result;
}
```

###Time Complexity is O(nlogn) for sorting and then checking n values in the array
