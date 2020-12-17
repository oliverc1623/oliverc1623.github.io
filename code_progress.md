---
layout: default
title: Code Progress
---

# Table of Contents

1. [Chapter 1](#chapter-1-arrays-and-strings)
	1. [Is Unique](#is-unique)
	2. [Check Permutation](#check-permutation)

## Chapter 1 Arrays and Strings

### Is Unique

```java
/* we'll make a hash table of booleans of size 128,
 representing each character in ASCII. Then, we'll 
 iterate through our word at each character and set 
 each index in our hash table to true. First check if 
 hash[i] is false, then set hash to true, otherwise return false. */ 

boolean isUnique(String s){
	boolean[] my_hash = new boolean[128];
	for(int i = 0; i <= s.length()-1; i++){
		int ascii_code = s.charAt(i);
		if(!my_hash[ascii_code]){
			my_hash[ascii_code] = true;
		} else {
			return false;
		}
	}
	return true; 
}

/* Sort the given string. Then, iterate the string with a window of size 2. 
If the characters within the window are the same return false otherwise keep 
sliding the window. This goes with the assumption that the string is in the 
alphabet TODO: make it work with non-alphabetic characters */

boolean isUnique(String s){
	String sorted_s = sort(s); // look up java string api
	for(int i = 0; i <= s.length()-2; i++){
		if(sorted_s.charAt(i) == sorted_s.charAt(i+1)){
			return false;
		}
	}
	return true;
}
```

---

### Check Permutation

```java
/* given two strings: use one of them make a hash map of booleans
 by setting the ascii code index to true; then iterate through the 
 second string and return false if a character is not in out hash map. */ 

boolean checkPermutation(){
	if(s1.length() != s2.length()){
		return false;
	}	
	boolean[] map = new boolean[128];
	for(int i = 0; i <= s1.length()-1; i++){
		map[s1.charAt(i)] = true;
	}
	for(int i = 0; i <= s2.length()-1; i++){
		if(!map[s2.charAt(i)]){
			return false;
		}
	}
	return true; 
}

/* 
Another thing we could try is first sort, "abcde" "bcdef", then iterate through length 
n and check if a string at i is not equal to the other string at i. 
Runtime of O(nlogn) -> space complexity is in place, if we use QuickSort. 
*/ 
boolean checkPermutation(String s1, String s2){
	if(s1.length() != s2.length()){
		return false;
	}	
	String s1_sorted = sort(s1); // write sort function later
	String s2_sorted = sort(s2);
	//we could just check if the strings are equal
	for(int i = 0; i <= s1.length()-1; i++){
		if(s1_sorted.charAt(i) != s2_sorted.charAt(i)){
			return false;
		}
	}
	return true; 
}
```
My solution is sloppy because we are using two separate for loop, both of length n. This would have a runtime of O(n).