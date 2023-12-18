Created by : seophohoho
Created time : 2023-11-19 16:11
Tags : #CS #OS
## What is Virtual Storage(Memory)?
- Non-Continuous allocation 기법을 사용
- 사용자 프로그램을 여러 개의 block으로 분할/관리
- 실행 시, 필요한 block들만 메모리에 적재
	- 나머지 block들은 swap device에 존재
### Address Mapping/Continuous allocation
- Relative address(상대주소)
	- 프로그램의 시작 주소를 0으로 가정한 주소
- Relocation(재배치)
	- 메모리 할당 이후, 할당된 주소(allocation address)에 따라서 Relative address(상대주소)들을 조정하는 작업
![[/OperatingSystem/img/img1.png]]
## AddressMapping/Non-Continuous allocation
- Virtual address(가상주소) = relative address
	- Logical address(논리주소)
	- 연속된 메모리 할당을 가정한 주소
- Real address(실제주소) = absolute(physical) address
	- 실제 메모리에 적제된 주소
- Virtual address -> Real address로 매핑
- User process는 실행 프로그램 전체가 메모리에 연속적으로 적재되었다고 가정하고 실행
![[3_Resource/OperatingSystem/img/img2.png]]
## BlockMapping
- 각 block에 대한 address mapping 정보 유지
- 해당 block에 대한 Virtual address 존재
	- v = (b,d)
	- b = block number
	- d = displacement(offset) in a block
- AddressMapping 정보를 관리하기 위해서 Block Map Table(BMT)가 존재
	- Kernel 공간에 Process마다 하나의 BMT를 가짐
![[3_Resource/OperatingSystem/img/img3.png]]
- BlockMapping의 실행 흐름은 다음과 같다.
	1. Process의 BMT에 접근
	2. BMT에서 block b에 대한 entry를 찾음
	3. Residence bit 검사
		1. if Residence bit = 0, swap device에서 해당 block을 메모리로 가져오고, BMT 업데이트 후 3-2 단계 수행
		2. if Residence bit = 1, BMT에서 block b에 대한 Real Address 값 a 확인
	4. 실제 주소 r 계산(r = a + d)
	5. r을 이용해서 메모리에 접근
![[3_Resource/OperatingSystem/img/img4.png]]
## Virtual Storage(Memory) Methods
- [[Paging-System]]
- [[Segmentation-System]]
- [[Hybrid-Paging-Segmentation-System]]
