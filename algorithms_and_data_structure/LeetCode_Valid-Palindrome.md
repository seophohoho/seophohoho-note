Created by : seophohoho  
Created datetime : 2023-12-28 13:59  
Tags : #Algorithm   
## Problem Info
URL : https://leetcode.com/problems/valid-palindrome/description/
## Solve_1
Runtime : 98ms. 
Memory : 23.73 MB. 
```python
def isPalindrome(self, s: str) -> bool:
	lists = []
	for i in range(len(s)):
		if(s[i].isalnum()):
			lists.append(s[i].lower())
	for i in range(len(lists)):
		if(lists[i] != lists[(len(lists)-1)-i]):
			return False
	return True
```
## Solve_2
Runtime : 295ms. 
Memory : 23.73 MB. 
```python
def isPalindrome(self, s: str) -> bool: 
	lists = [] 
	for char in s: 
		if(char.isalnum()): 
			lists.append(char.lower()) 
		while len(lists) > 1: 
			if lists.pop() != lists.pop(0): 
				return False 
	return True
```
## Solve_3
Runtime : 80~109ms. 
Memory : 22.xx MB. 
```python
def isPalindrome(self, s: str) -> bool:
	deque = collections.deque()
	for char in s:
		if(char.isalnum()):
			deque.append(char.lower())
	while len(deque) > 1:
		if deque.popleft() != deque.pop():
			return False
	return True
```
## Solve_4
Runtime : 30ms. 
Memory : 18.87 MB. 
```python
def isPalindrome(self, s: str) -> bool:
	s = s.lower()
	# 정규식으로 불필요한 문자 필터링
	s = re.sub('[^a-z0-9]','',s)
	return s == s[::-1] ##슬라이싱
```