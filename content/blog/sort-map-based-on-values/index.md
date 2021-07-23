---
title: Sort HashMap based on Values
date: "2021-07-23T22:40:32.169Z"
description: Sort HashMap based on Values
---
Doing these using COmparator and STreams

```java
public static HashMap<String,Integer> sortByValue(HashMap<String,Integer> map)
{
    List<Map.Entry<String,Integer>> list=new LinkedList<Map.Entry<String,Integer>>(map.entrySet());
    Collections.sort(list,(o1,o2)->o1.getValue().compareTo(o2.getValue()));
    HashMap<String,Integer> new_map=new LinkedHashMap<String,Integer>();
    for(Map.Entry<String,Integer> entry:list){
         new_map.put(entry.getKey(),entry.getValue());
    }
    //return new_map;
    return map.entrySet().stream()
    .sorted((o1,o2)->o1.getValue().compareTo(o2.getValue())).
    collect(Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue,
    (e1,e2)->e1,LinkedHashMap::new));
}
```