Created by : seophohoho  
Created datetime : 2024-03-30 18:12  
Tags : #about_computer 
## What is context??
- 프로세스와 관련된 정보들의 집합
	- CPU register context in CPU
	- Code & data, Stack, PCB in memory
## What is context saving??
- 현재 process의 CPU 안에 있는 Register context 를 [[PCB]]에 저장하는 작업
## What is context restoring??
- Register context를 process로 복구하는 작업
## What is context switching??
실행 중인 process의 context를 [[PCB]]로 저장하고, 앞으로 실행 할 process의 context [[PCB]]로 부터 복구 하는 일.  
즉, `context saving + context switching` 이 함께 일어난다.
## context switching overhead
- context switching에 소요되는 비용은 OS마다 다름.
- context switching은 OS의 성능에 큰 영향을 끼친다.
- **즉, 불필요한 context switching을 줄이는 것이 중요하다.**
	- 이를 위해서 [[thread]]를 사용한다.
