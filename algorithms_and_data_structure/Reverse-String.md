Created by : seophohoho  
Created datetime : 2024-01-04 11:04  
Tags : #Algorithm #String   
## Problem Info
Url : https://leetcode.com/problems/reverse-string/
## Solve_1
투 포인터를 이용한 방법.  
```python
def reverseString(self, s: List[str]) -> None:
	left,right = 0,len(s)-1
	while left < right:
		s[left],s[right] = s[right],s[left]
		left = left+1
		right = right-1
```
## Solve_2
파이썬다운 방식.  
```python
def reverseString(self, s: List[str]) -> None:
	s.reverse()
```
