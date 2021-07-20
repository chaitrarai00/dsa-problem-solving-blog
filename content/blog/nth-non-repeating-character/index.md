---
title: nth Non Repeating Permutation
date: "2021-07-20T22:40:32.169Z"
description: The problem statement is to find the nth non repeating character from a given String
---

##Given a strings, and a value n find the nth non repeating character ( like find the 3rd non repeating character)

public static char fun(String str1, int n)
{
Set<Character> set=new LinkedHashSet<Character>();
for(int i=0;i<str1.length();i++){
if(set.contains(str1.charAt(i)))
set.remove(str1.charAt(i));
set.add(str1.charAt(i));
}
char[] string_new=set.toArray(new char[set.size()]);
return string_new[3];
}
public static void main (String[] args) {
String str1 = "Chaitra";
int n=3;
System.out.println(fun(str1,3));
//code
}
}
