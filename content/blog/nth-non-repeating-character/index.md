---
title: nth Non Repeating Permutation
date: "2021-07-21T22:40:32.169Z"
description: The problem statement is to find the nth non repeating character from a given String
---

##Given a strings, and a value k find the kth non repeating character ( like find the 3rd non repeating character)

> This problem for the nth repeating character in string has 2 things one would have to take into consideration

> one that the count has to be in check and two the index also has to be in check to get the kth repeating character

> We create a new class/ structure to store count and index together, we will use this to store the count and recent index of each character

> next we will store each character as key in a Hashmap and value as the CountIndex of the character

```java
 public class Countindex{
        public int index;
        public int count;
        public Countindex(int index){
            this.index=index;
            this.count=1;
        }
        public void inccount(){
            this.count++;
        }
    }

    public char fun(String str,int k)
    {
        Map<Character,Countindex> map=new LinkedHashMap<>();
        for(int i=0;i<str.length();i++){
            if(map.containsKey(str.charAt(i)))
                map.get(str.charAt(i)).inccount();
            else
                map.put(str.charAt(i),new Countindex(i));
        }
        for(char c:map.keySet())
        {
            if(map.get(c).count==1 && map.get(c).index==k-1)
            return c;
        }
        return '\0';
    }
```

###The time complexity would be O(n) for storing values in hashmap and to retrieving the appropriate value from map O(1). So total complexity is O(n)
