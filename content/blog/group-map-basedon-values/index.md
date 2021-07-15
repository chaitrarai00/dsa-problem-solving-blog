---
title: Hroup Keys Based on Values
date: "2021-07-15T22:40:32.169Z"
description: The problem statement is to group the keys based on values one sees
---

##Say you have a map {a:1, b:2, c:3, d:1, e:1, f:2} we need the output in terms of groups based on the values of keys in map

> 1:a,d,e
> 2:b,f
> 3:c

```java
public static void fun(Map<Character,Integer> map)
{
  Map<Integer,List<Character>> new_map=new HashMap<Integer,List<Character>>();
  for(Map.Entry<Character,Integer> entry: map.entrySet()){
  List<Character> groups=new ArrayList<Character>();
  if(new_map.containsKey(entry.getValue()))
      groups=new_map.get(entry.getValue());
  groups.add(entry.getKey());
  new_map.put(entry.getValue(),groups);
  }
  System.out.println(new_map);
}
```

##We create a new_map to get the groups with respect to values so space complexity for this is O(n) and we do this by storing the keys in a list again a space complexity of O(n) that is O(n)+O(n). The time complexity of iterating through the map would be O(n)

> We first for throught the array and decide to create a new map with a Integer, List type key value pair
> They are <The value from given map, List of keys in given map>
> We keep adding the keys of each unique value into the list groups which is now the value
> Now that the values are the new keys they are unique and stores list of the keys you havd previously giving us:
> {1=[a, d, e], 2=[b, f], 3=[c]}
> Now lets try to eliminate the boilerplate code using Java 8 streams

```java
 public static void fun(Map<Character,Integer> map)
    {
    Map<Integer,List<Character>> new_map=map.entrySet().stream().collect(Collectors.
    groupingBy(Map.Entry::getValue,Collectors
    .mapping(Map.Entry::getKey,Collectors.toList())));
    System.out.println(new_map);
    }
```

##Same Operations same time complexity but all operations are done lazily in streams

> Collectors.groupingBy takes the values a function and based on functions groups collects new map
> The new map uses Collectors.mapping to map for each key and make a list of old keys as values
> groupingBy(Function<? super T,? extends K> classifier)Returns a Collector implementing a "group by" operation on input elements of type T, grouping elements according to a classification function, and returning the results in a Map.
> mapping(Function<? super T,? extends U> mapper, Collector<? super U,A,R> downstream)Adapts a Collector accepting elements of type U to one accepting elements of type T by applying a mapping function to each input element before accumulation.
