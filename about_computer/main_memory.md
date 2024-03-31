Created by : seophohoho  
Created datetime : 2024-03-23 18:41
Tags : #about_computer
## INTRO
- 프로시저가 수행하기 위해서 프로그램과 데이터를 저장하는 공간입니다.
- RAM이라고 불립니다.
- RAM은 SRAM(Static RAM)과 DRAM(Dynamic RAM)으로 분류할 수 있습니다.
- 흔히 DRAM을 사용합니다.
## 왜 Main Memory를 사용할까?
디스크 입출력 병목현상(I/O bottleneck)를 해소하기 위해서입니다.
## 왜 DRAM을 사용할까?
첫번째로, 속도 때문입니다.  
DRAM은 SSD보다 속도가 빠르지만, SRAM보다는 속도가 느립니다. 그러면, 단순히 속도를 보았을 경우에는 SRAM이 월등히 빠를텐데, 왜 DRAM을 사용할까요?
두번째로, 비용 때문입니다.  
DRAM은 SRAM보다 비트당 가격이 더 저렴합니다. DRAM과 SRAM을 동일한 용량에서 비교했을 경우, DRAM이 비용면에서 더 저렴한 것을 볼 수 있습니다.
세번째로, 밀도차이 때문입니다.
DRAM의 셀은 SRAM의 셀보다 더 작습니다. 셀이 더 작을 경우, 단위 면적당 더 많은 셀들을 집적시킬 수 있기 때문에, DRAM이 SRAM보다 더 많은 데이터를 저장시킬 수 있습니다.
## DRAM과 SRAM 비교
DRAM과 SRAM을 비교하자면, 다음과 같습니다.

| SRAM                                                    | DRAM                                               |
| ------------------------------------------------------- | -------------------------------------------------- |
| SRAM은 DRAM에 비해 액세스 시간이 더 짧습니다.                          | DRAM은 액세스 시간이 더 높습니다. SRAM보다 느립니다.                 |
| SRAM은 DRAM보다 비쌉니다.                                      | DRAM 비용은 SRAM에 비해 저렴합니다.                           |
| SRAM은 지속적인 전원 공급이 필요하지만 전력 소비가 적습니다.                    | DRAM은 정보가 커패시터에 저장되므로 더 많은 전력 소비가 필요합니다.           |
| SRAM은 낮은 패키징 밀도를 제공합니다.                                 | DRAM은 높은 패키징 밀도를 제공합니다.                            |
| 트랜지스터와 래치를 사용합니다.                                       | 커패시터와 매우 적은 수의 트랜지스터를 사용합니다. 즉, SRAM보다는 구현이 간단합니다. |
| L2 및 L3 CPU [[cache_memory]] 장치는 SRAM의 일반적인 응용 프로그램입니다. | DRAM은 주로 컴퓨터의 메인 메모리로 사용됩니다.                       |
| SRAM의 저장 용량은 1MB~16MB입니다.                               | DRAM의 저장 용량은 1GB~16GB입니다.                          |
| SRAM은 온칩 메모리 형태입니다.                                     | DRAM은 오프칩 메모리 형태입니다.                               |
| SRAM은 프로세서에서 널리 사용되거나 컴퓨터의 주 메모리와 프로세서 사이에 위치합니다.       | DRAM은 메인보드에 위치합니다.                                 |
| SRAM은 크기가 더 작습니다.                                       | DRAM은 더 큰 저장 용량을 사용할 수 있습니다.                       |
| SRAM은 스위치를 통해 전류 방향을 변경하는 원리로 작동합니다.                    | DRAM은 전하를 유지하는 데 작동합니다.                           |
## 레퍼런스
- https://www.chip1stop.com/sp/knowledge/054_types-and-featurs-of-memory_ko
- https://m.yes24.com/Goods/Detail/69761003 (개정5판, p238~p240)
- https://www.chip1stop.com/sp/knowledge/054_types-and-featurs-of-memory_ko
- https://www.youtube.com/watch?v=EdTtGv9w2sA&list=PLBrGAFAIyf5rby7QylRc6JxU5lzQ9c4tN&index=1


