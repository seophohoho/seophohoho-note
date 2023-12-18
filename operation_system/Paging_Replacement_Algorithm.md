Created by : seophohoho  
Created time : 2023-11-21 06:57  
Tags : #CS #OS 
## FIFO Algorithm
- First In First Out
	- 가장 오래된 page를 교체
- Page가 적재 된 시간을 기억해야 한다
- 자주 사용되는 page가 교체 될 가능성이 높다
- FIFO anomaly(Belady's anomaly)
	- FIFO Algorithm은 더 많은 page frame을 할당 받음에도 불구하고 page fault의 수가 증가하는 경우가 있음.
![[img22.png]]
![[img24.png]]
## Optimal Replacement Algorithm(최적 교체)
- 1966년 Belady가 제시
- 앞으로 가장 오랫동안 참조되지 않을 page 교체
	- Tie-breaking rule = page 번호가 가장 큰/작은 페이지 교체
- 이론상으로는 모든 replacement algorithm 중 page fault가 가장 적다
- 실현 불가능한 기법
	- Page reference string을 미리 알고 있어야 한다.
## LRU(Least Recently Used) Algorithm
- 가장 오랫동안 참조되지 않은 page를 교체(locality에 기반을 두었다)
- page 참조 시 마다 시간을 기록해야 한다.(overhead가 발생)
- Optimal Replacement Algorithm(최적 교체)에 근접한 성능을 보여줌
- 실제로 가장 많이 활용되는 기법
![[img23.png]]
## Clock or Second Chance Algorithm
- Page frame들을 순차적으로 가리키는 pointer(시계바늘)를 사용해서 교체될 page 결정
- Reference bit 사용함
![[img26.png]]
- Clock Algorithm 다음과 같은 실행 순서를 가진다.
	- 현재 가리키고 있는 page의 reference bit를 확인
	- if r = 0, 교체 page로 결정
	- if r = 1, reference bit 초기화 후 Pointer 이동
![[img27.png]]
## LFU(Least Frequently Used) Algorithm
- 가장 참조 횟수가 적은 page를 교체
- Page 참조 시 마다, 참조 횟수를 누적시켜야 한다.
- Locality 활용
	- LRU(Least Recently Used)에 비해서 적은 overhead를 가진다.
- 하지만, 최근 적재된 참조될 가능성이 높은 page가 교체 될 가능성이 있다
- 참조 횟수 누적 overhead가 발생.
![[img25.png]]

