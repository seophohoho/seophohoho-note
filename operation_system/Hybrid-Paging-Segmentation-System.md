Created by : seophohoho
Created time : 2023-11-21 02:10
Tags : #CS #OS 
## What is Hybrid-Paging-Segmentation-System?
- Paging과 Segmentation의 장점 결합
- 프로그램 분할
	1. 논리 단위의 segment로 분할
	2. 각 segment를 고정된 크기의 page들로 분할
- Page 단위로 메모리에 적재
![[img17.png]]
## Address mapping
- Virtual address : v = (s,p,d)
	- s : segment number
	- p : page number
	- d : offset in a page
- SMT와 PMT 모두 사용
	- 각 프로세스마다 하나의 SMT
	- 각 segment마다 하나의 PMT
- Address mapping mechanism
	- Direct
	- associated
- SMT in hybrid mechanism
![[img18.png]]
- PMT for a segment k in hybrid mechanism
![[img19.png]]
![[img20.png]]
## Direct mapping
![[img21.png]]
## Conclusion
- 논리적 분할(segment)와 고정 크기 분할(page)을 결합한 것이 Hybrid-Paging-Segmentation-System
	- 장점:
		- page sharing/protection이 쉽다
		- 메모리 할당/관리 overhead가 작다
		- No external fragmentation
	- 단점:
		- 전체 테이블 수 증가
			- 메모리 소모가 큼
			- Address mapping 과정 복잡성 상승
		- Direct mapping일 경우에는, 메모리 접근이 3배
			- 성능이 저하될 수 있음
## Paging-Replacement-Algorithm
[[Paging-Replacement-Algorithm]]

