Created by : seophohoho  
Created datetime : 2023-12-28 13:59  
Tags : #Algorithm #String
## Problem Info
URL : https://leetcode.com/problems/valid-palindrome/description/
## Solve_1
```python
def isPalindrome(s: str) -> bool:
	strs=[]
	for char in s:
	if char.isalnum():
	strs.append(char.lower())
	while len(strs)>1:
	if strs.pop(0) != strs.pop(): #strs.pop(0)은 가장 앞에 위치한 원소를 제거하고, 모든 원소를 앞 당긴다.
	return False
	return True
```
Time Complexity : O(n^2). 
`strs.pop(0)` 은 한 번 수행될 때마다 나머지 요소들이 한 칸씩 앞으로 이동한다. 그렇기에 시간복잡도 O(n)을 가진다.
## Solve_2
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
Time Complexity : O(n). 
## Solve_3
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
Time Complexity : O(n). 
컨테이너(container)의 양끝 엘리먼트(element)에 접근하여 삽입 또는 제거를 할 경우, 일반적인 리스트(list)가 이러한 연산에 O(n)이 소요되는 데 반해, 데크(deque)는 O(1)로 접근 가능하다.
## Solve_4
```python
def isPalindrome(self, s: str) -> bool:
	s = s.lower()
	# 정규식으로 불필요한 문자 필터링
	s = re.sub('[^a-z0-9]','',s)
	return s == s[::-1] ##슬라이싱
```
Time Complexity : O(n)  
`re`는 Regular Expression의 약자로 정규표현식이다. 