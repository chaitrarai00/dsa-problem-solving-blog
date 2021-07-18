---
title: First Unique character in a String
date: "2021-07-15T22:40:32.169Z"
description: The problem statement is to find the first repeating number in a given input array
---

##find the first repeating number in a given input array:[1,2,2,3] and [1,2,3,3]

> Seeing the input it seems like all the input values have a good index based storage

> lets assume we get a count array of size= length of array+1(n+1)

```java
 public static void fun(int a[])
    {
        int[] count=new int[a.length+1];
       for(int i=0;i<a.length;i++){
           if(count[a[i]]==1)
            System.out.println(a[i]);
           count[a[i]]++;
       }
    }
```

##these would have O(n+1) space complexity and O(n) time complexity. This solution also has many problem and works only when the values are close to the array length. For instance it wont work for [2,3,4,5,6,9,9] and many such inputs

> may be we can iterate and compare with the next elemnt each time.

> we can expect accuracy here

```java
 public static void fun(int a[])
    {
       for(int i=0;i<a.length-1;i++){
           if(a[i]==a[i+1])
            System.out.println(a[i]);
       }
    }
```

##The time complexity is O(n), there would be each elemnt getting compared with the element next to it

> Lets try putting in HashSet or Hashmaps or may be both

> Hashmap where the count is stored as value and the key being the number present

```java
public static void fun(int a[])
{

  Map<Integer,Integer> map=new HashMap<Integer,Integer>();
  for(int i=0;i<a.length;i++){
    if(map.containsKey(a[i]))
        System.out.println(a[i]);
        map.put(a[i],1);
      }
}
```

##The Time complexity is O(n) for n elements to be added in the Hashmap and since its underlying store is a list of index its 1\*(n) for n insertions using Treemap will use nLogn where log1+log2+..+logn for each insertion with underlying tree

> But wait we dont need a count a key value combination is again unnecessary as we just have to print the first repeated element

> Lets use a HashSet instead where we add all the elements to the set and then check if the values exist

```java
public static void fun(int[] a)
    {
    Set<Integer> set=new HashSet<Integer>();
    for(int i=0;i<a.length;i++){
         if(set.contains(a[i]))
            System.out.println(a[i]);
         set.add(a[i]);
       }
    }
```

##This has a O(n) time complexity and O(n) space complexity
