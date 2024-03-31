Created by : seophohoho  
Created datetime : 2024-03-30 16:08  
Tags : #about_computer   
## What PCB(Process Control Block)
- OS(즉, Kernel이)가 [[process]] 관리에 필요한 정보를 저장.
- [[process]] 생성 시, 생성 됨.
![[pcb_1.png]]
## PCB information
- PID(Process Identification Number)
	- 프로세스 고유 식별 번호
- 스케줄링 정보
	- 프로세스 우선순위 등과 같은 스케줄링 관련 정보들
- 프로세스 상태
	- 자원 할당, 요청 정보
- 메모리 관리 정보
	- Page table, Segment table 등
- 입출력 상태 정보
	- 할당 받은 입출력 장치, 파일 등에 대한 정보 등
- 문맥 저장 영역(Context Save Area)
	- 프로세스의 레지스터 상태를 저장하는 공간 등
- 계정 정보
	- 자원 사용 시간 등을 관리
**PCB 정보는 OS 마다 서로 다르다.**
**PCB 참조 및 갱신 속도는 OS 성능을 결정 짓는 중요한 요소 중 하나이다.**
