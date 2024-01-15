Created by : seophohoho  
Created datetime : 2024-01-13 15:44  
Tags : #Algorithm #String 
## Problem Info
Url: https://leetcode.com/problems/reorder-data-in-log-files/
## Solve_1
```python
def reorderLogFiles(self, logs: List[str]) -> List[str]:
	letter_logs,digit_logs = [],[]
	for log in logs:
		if log.split()[1].isdigit():
			digit_logs.append(log)
		else:
			letter_logs.append(log)
	letter_logs.sort(key=lambda x:(x.split()[1:],x.split()[0]))
	return letter_logs+digit_logs
```


