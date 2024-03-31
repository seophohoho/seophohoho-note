Created by : seophohoho  
Created datetime : 2024-03-30 18:01  
Tags : #about_computer 
## What is interrupt??
- Unexpected
- external events
## interrupt Types
- I/O interrupt
- Clock interrupt
- Console interrupt
- Program check interrupt
- Machine check interrupt
- Inter-process interrupt
- System call interrupt
## interrupt progress
![[interrupt_progress.png]]
1. interrupt 발생
2. process 중단(커널의 개입으로)
3. interrupt handling
	1. interrupt 발생 장소 및 원익 파악
	2. interrupt service 결정
4. interrupt service
	1. interrupt service routine(ISR) call