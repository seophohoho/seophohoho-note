Created by : seophohoho
Created time : 2023-11-19 18:30
Tags : #CS #OS 
## What is Paging-System?
- 프로그램을 같은 크기의 블록으로 페이지들(pages)로 분할 한 것
- 페이지(page)는 프로그램의 분할된 block
- 페이지프레임(page frame)은 ``
	- 메모리의 분할 영역을 말하고
	- page와 같은 크기로 분할
![[3_Resource/OperatingSystem/img/img5.png]]
- 논리적 분할이 아님(크기에 따른 분할)
	- page 공유(sharing) 및 보호(protection) 과정이 복잡
- Simple and Efficient
- No External Fragmentation
	- But, Internal Fragmentation 발생
## Address Mapping
- Virtual Address
	- v = (p,d)
		- p = page number
		- d = displacement = offset
- Address Mapping은 PMT(Page Map Table) 사용
![[3_Resource/OperatingSystem/img/img6.png]]
## Address Mapping/mechanism
- Direct mapping
- Associative mapping
	- TLB(Translation Look-aside Buffer)
- Hybrid direct associative mapping
### Address Mapping/mechanism/Direct mapping
- Block mapping 방법과 유사
- 이러한 것을 가정해보자.
	- PMT를 Kernel 안에 저장
	- PMT entry size = entrysize
	- Page size = pagesize
- Direct mapping 다음과 같은 실행 흐름을 가진다
	1. process의 PMT가 저장되어 있는 시작 주소 b에 접근
	2. 해당 PMT에서 page p에 대한 entry 찾음(p의 entry 위치 = b + p x entry size)
	3. 찾아진 entry p의 존재 비트 검사
		1. if Residence bit = 0, swap device에서 해당 page를 메모리에 적재, PMT를 업데이트 한 후 3-2 단계 수행(=이를 page fault라고 한다. 하지만 Context switching이 발생하여 overhead가 발생한다. 즉, page fault는 피해야 한다)
		2. if Residence bit = 1, 해당 entry에서 page frame 번호 p'를 확인
	4. p'(page frame)와 가상 주소 offset d를 이용해서 실제 주소 r를 계산
		1. r = p' * page size + d
	5. 실제 주소 r로 메모리에 접근
![[3_Resource/OperatingSystem/img/img7.png]]
- 하지만, Direct mapping 다음과 같은 문제점을 가지고 있었다.
	- Kernel 영역에 있는 PMT 접근 -> 유저 영역에 있는 실제 주소에 접근이기 때문에, 메모리 접근 횟수가 2배가 된다.(performance degradation, 성능 저하가 발생한다)
	- PMT를 위한 메모리 공간이 필요하게 된다.
- Solution
	- Associative mapping (TLB)
	- PMT를 위한 전용 기억장치(공간) 사용
	- Dedicated register or cache memory
	- Hierarchical paging
	- Hashed page table
	- Inverted page table
### Address Mapping/mechanism/Associative mapping
- TLB(Translation Look-aside Buffer)에 모든 process의 PMT를 적재
- PMT를 병렬 탐색
- Low overhead, high speed
- But, Expensive hardware(memory cache)
	- 크기가 큰 PMT를 다루기는 어렵다.(아래 링크의 Typical TLB 확인)
- https://en.wikipedia.org/wiki/Translation_lookaside_buffer
![[3_Resource/OperatingSystem/img/img8.png]]
### Address Mapping/mechanism/Hybrid-Direct-Associative-Mapping
- Direct mapping과 Associative mapping을 혼합하여 사용
	- 이를 통해서 hardware 비용 줄이고, Associative mapping의 장점을 활용
- 작은 크기의 TLB 사용
	- PMT =  Kernel에 저장
	- TLB = PMT 중 일부 entry들을 적재
		- 가장 최근에 사용된 page들에 대한 entry 저장
- Hybrid-Direct-Associative-Mapping의 실행 흐름은 다음과 같다.
	1. (first trial) if TLB에 적재, residence bit = 1 검사하고, page frame 번호 확인
	2. (second trial) if TLB에 적재 되지 않음, Direct mapping으로 page frame 번호 확인. 해당 PMT entry를 TLB에 적재
![[img9.png]]
## Memory Management
- Page와 같은 크기(page frame)로 미리 분할 하여 관리/사용
- FPM(Fixed Partition Memory, 고정 분할 기억장치 할당) 기법과 유사
- 분할한 page frame들에 대한 정보를 담기 위해서 Frame table 등장
	- Frame table은 Page frame당 하나의 entry 가진다.
	- 구성은 다음과 같다.
		- Page frame number
		- Allocated/available field(사용 중인 page frame인지 체크하는 값)
		- PID field
		- Link field = For free list(사용 가능한 빈 page frme들을 연결)
		- AV = Free list header(빈 page frame을 searching 하기 위한 포인터)
![[img10.png]]
## Page Sharing
- 여러 프로세스가 특정 page를 공유 가능
	- Non-continuous allocation이기 때문에 가능한 일이다.
		- continuous allocation의 경우에는 메모리에 해당 프로그램의 모든 코드가 순차적으로 로드되는 것이기 때문에, 특정 코드를 Sharing 하는 것은 어려운 일
- Sharing 가능한 page는 다음과 같다.
	- Procedure pages
		- Pure code(reenter code)
	- Data page
		- Read-only data
		- Read-write data
			- 병행성(concurrency) 제어 기법 관리하에서만 가능 -> 여러 프로세스가 하나의 변수를 변경하게 된다면, 흐름이 꼬일수도 있기 때문
## Page Protection
여러 프로세스가 page를 공유 할 때, Protection bit를 사용![[img11.png]]
![[img11.png]]
