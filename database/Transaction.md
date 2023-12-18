Created by : seophohoho
Created time : 2023-12-08 21:10
Tags : #CS #DB 
## What is Transaction?
- 단일한 논리적인 작업 단위(A single logical unit of work).
- 논리적인 이유로 여러 SQL문들을 단일 작업으로 묶어서 나눠질 수 없게 만든 것.
## Transaction의 성질
- 트랜잭션은 다음의 ACID 성질을 가지고, DBMS의 동시성 제어와 회복 기법을 통해서 유지된다.
- Atomicity(원자성)
- Consistency(일관성)
- Isolation(독립성,고립성)
- Durability(지속성) or Permanency(영속성)
### Transaction의 성질/Atomicity
- All or NOTHING
- Transaction은 모두가 성공하거나, 전혀 수행 되지 않아야 한다.
- Transaction은 논리적으로 쪼개질 수 없는 작업 단위이기 때문에 내부의 SQL문들이 모두 성공해야 한다.
- 중간에 SQL문이 실패하면, 지금까지의 작업이 모두 취소해서 아무 일도 없었던 것처럼 rollback 한다.
### Transaction의 성질/Consistency
- Transaction은 DB 상태를 consistent 상태에서 또 다른 consistent 상태로 바꿔야 한다.
- constraints, trigger 등을 통해서 DB에 정의된 rules을 transaction이 위반했다면, rollback 해야 한다.
- Transaction이 DB에 정의된 rule을 위반했는지는 DBMS가 commit 전에 확인하고 알려준다.
### Transaction의 성질/Isolation
- 여러 Transaction들이 동시에 실행될 때도 혼자 실행되는 것처럼 동작하게 만든다.
- DBMS는 여러 종류의 Isolation level을 제공한다.
- 개발자는 isolation level 중에서 어떤 level로 Transaction을 동작시킬지 설정할 수 있다.
- concurrency control의 주된 목표가 Isolation이다.
- 고립성에는 등급이 있는데, 다음과 같다.
	- 0등급: 상위등급 Transaction의 temporary update(or dirty read) problem을 덮어쓰지 않는다.
	- 1등급: lost update problem가 없다.
	- 2등급: lost update problem과 temporary update(or dirty read) problem가 없다.
	- 3등급: 2등급의 성질을 모두 가지며, 이외에도 반복 읽기 성질을 가진다.
### Transaction의 성질/Durability
- commit된 Transaction은 DB에 영구적으로 저장한다.
- 즉, DB system에 문제(Power fail or DB Crash)가 생겨도 commit된 Transaction은 DB에 남아 있는다.
- '영구적으로 저장한다'라고 할 때는 일반적으로 비휘발성 메모리에 저장하는 것을 의미한다.
- 기본적으로 Transaction의 durability는 DBMS가 보장한다.
## Transaction의 상태
- Active(수행 중)
- Partially Committed(부분 완료)
- Committed(완료)
- Failed(실패)
- Aborted(철회)
정상적으로 수행 중인 Transaction이 모든 문장을 실행하고 나면 Partially Committed(부분 완료) 상태가 되고, 안전한 저장 장치에 로그 쓰기 작업 등이 끝나게 되면, Committed(완료) 상태가 된다.
그러나 도중 Transaction 실행에 문제가 발생한다면, Failed(실패) 상태가 되고, 복구해야 할 것들을 복구한 뒤에 Aborted(철회) 상태가 된다.
또는 Transaction 실행 도중에 사용자 요청에 의해 실행 취소 상태가 되기도 한다.
![[3_Resource/DataBase/img/img6.png]]
## 동시성
운영체제의 다중 프로그래밍에 의해서 여러 사용자가 데이터베이스에 동시 접근 가능. 
이를 위해서, Transaction을 동시에 처리해야 하는데, 모든 사용자 요구에 대해서 결과가 일관성을 가져야 한다.
프로세서(CPU)의 개수가 1개라면, 인터리빙(interleaving) 형태의 동시성을 가짐.
프로세서(CPU)의 개수가 1개 이상이라면, 다중 프로세싱에 의한 동시성을 가짐.
![[3_Resource/DataBase/img/img1.png]]
## 동시성 제어가 필요한 이유
운영체제의 다중 프로그래밍에 의해서 여러 사용자가 데이터베이스에 동시 접근 가능. 이를 위해서 Transaction을 동시에 처리해야 하는데, 모든 사용자 요구에 대해서 결과가 일관성을 가져야 한다. 따라서 일관성 있는 병행처리를 위해서 동시성 제어가 필요.
<U>적절한 제어</U>가 없는 상태로 동시성 제어를 진행할 때의 문제점은 다음과 같다.
- Lost Update Problem
- Temporary Update(or Dirty Read) Problem
- Incorrect Summary Problem
- Unrepeatable Read Problem
- Phantom Read Problem
이를 해결하기 위해서는 동시성 제어 기법이 필요.
### 동시성 제어가 필요한 이유/Lost Update Problem
동일한 데이터베이스 항목들에 접근하는 두 Transaction의 연산들이 인터리빙(interleaving)된 형태로 실행되어서 어떠한 데이터베이스 항목의 값을 틀리게 만들 때 발생.
![[3_Resource/DataBase/img/img4.png]]
과정은 다음과 같다.
1. T1 reads the value of A (= 10 say).
2. T2 updates the value to A (= 15 say) in the buffer.
3. T2 does blind write A = 25 (write without read) in the buffer.
4. T2 commits.
5. When T1 commits, it writes A = 25 in the database.
### 동시성 제어가 필요한 이유/Temporary Update(or Dirty Read) Problem
하나의 Transaction이 하나의 데이터베이스 항목을 갱신한 후에 어떤 이유로 인해서 그 트랜잭션(transaction)이 실패하고, 갱신된 항목을 원래의 값으로 되돌리기 전에 다른 Transaction이 그 갱신된 항목에 접근한 경우에 발생.
![[3_Resource/DataBase/img/img2.png]]
과정은 다음과 같다.
1. T1 reads the value of A.
2. T1 updates the value of A in the buffer.
3. T2 reads the value of A from the buffer.
4. T2 writes the updated the value of A.
5. T2 commits.
6. T1 fails in later stages and rolls back
### 동시성 제어가 필요한 이유/Incorrect Summary Problem
한 Transaction이 여러 데이터베이스 항목들에 대해서 그룹 함수를 실행하고, 다른 Transaction들이 그 항목들 중에서 일부를 갱신하고 있다면, 결과가 반영되지 않는 경우를 말한다.
### 동시성 제어가 필요한 이유/Unrepeatable Read Problem
트랜잭션 T1가 수행 도중에 동일한 항목을 2번 읽는데, 그 2번의 읽기 연산 사이에 다른 트랜잭션 T2가 해당 항목의 값을 바꾸는 것.
![[3_Resource/DataBase/img/img3.png]]
과정은 다음과 같다.
1. T1 reads the value of X (= 10 say).
2. T2 reads the value of X (= 10).
3. T1 updates the value of X (from 10 to 15 say) in the buffer.
4. T2 again reads the value of X (but = 15).
### 동시성 제어가 필요한 이유/Phantom Read Problem
Transaction이 버퍼에서 어떤 변수를 읽은 후 나중에 같은 변수를 읽을 때 해당 변수가 존재하지 않는 것을 발견할 때 발생
![[3_Resource/DataBase/img/img5.png]]
과정은 다음과 같다.
1. T1 reads X.
2. T2 reads X.
3. T1 deletes X.
4. T2 tries reading X but does not find it.
## 데이터베이스의 read, write 연산
- read_item(x)의 수행과정
	1. 항목 x를 포함하는 디스크 블록의 주소를 찾는다.
	2. if 디스크 블록이 주기억장치의 버퍼에 존재하는 것이 아니라면, 디스크 블록을 주기억장치의 버퍼로 복사한다.
	3. 항목 x를 버퍼로부터 프로그램 변수 x에 복사한다.
- write_item(x)의 수행과정
	1. 항목 x를 포함하는 디스크 블록의 주소를 찾는다.
	2. if 디스크 블록이 주기억장치의 buffer에 존재하는 것이 아니라면, 디스크 블록을 주기억장치의 버퍼로 복사한다.
	3. 항목 x를 프로그램 변수 x에서 버퍼의 정확한 위치로 복사한다.
	4. 갱신(Update)된 블록을 디스크에 저장한다.
## Transaction들의 스케쥴(히스토리)
Transaction들이 인터리빙(interleaving) 방식으로 동시에 수행될 때, 모든 Transaction들의 연산들의 실행 순서를 스케줄(Schedule)이라고 한다.
## 스케쥴의 직렬가능성
- Serial Schedule(직렬 스케쥴)
- NonSerial Schedule(비직렬 스케쥴)
- Serializable Schedule(직렬 가능한 스케쥴)
- Conflict
### 스케쥴의 직렬가능성/Serial Schedule
- 인터리빙 방식을 이용하지 않고 각 트랜잭션 별로 연산들을 순차적으로 실행.
- 모든 트랜잭션이 완료될 때까지 다른 트랜잭션의 방해를 받지 않고 독립적으로 수행되기 때문에, 트랜잭션의 성질 중 Isolation이 높다.
- 하지만, 트랜잭션이 독립적으로 수행하기 때문에, 병행 수행이라고 할 수 없다. 즉, 데이터베이스 처리량의 관점에서 보자면 효율적인 방식은 아니기 때문에, 잘 사용하지 않는다고 한다.
![[3_Resource/DataBase/img/img7.png]]
### 스케쥴의 직렬가능성/Nonserial Schedule
- 인터리빙 방식을 이용해서 트랜잭션을 병행해서 수행시키는 것.
![[3_Resource/DataBase/img/img8.png]]
### 스케쥴의 직렬가능성/Conflict
- 두 개의 연산이 각각 상이한(다른) 트랜잭션에 속하고 있으면서 동일한 데이터 아이템을 처리 대상으로 하고 있고, 적어도 하나의 연산은 기록 연산이 되는 경우.
- 다수 트랜잭션이 실행 순서 변경에 따라서 값이 달라지는 현상.
### 스케쥴의 직렬가능성/Result Equivalent
- 동일한 초기 상태에서 두 개의 상이한(다른) 스케쥴로 생성된 데이터베이스의 최종 결과가 모두 똑같은 경우.
### 스케쥴의 직렬가능성/Serializable Schedule
- N개의 Transaction으로 구성된 비직렬 스케쥴 S가 동일한 N개의 Transaction으로 구성된 어떤 직렬 스케쥴과 동치(equivalent)일 경우.
- 하나의 트랜잭션이 데이터를 독점하는 것과 같은 동일한 결과를 얻는 성질.
### 스케쥴의 직렬가능성/Conflict Serializability
- 다수 트랜잭션이 수행되더라도 하나의 트랜잭션이 독점적으로 수행되는 것과 동일한 결과를 얻을 수 있도록 충돌을 회피하는 기법.
## Reference
https://www.gatevidyalay.com/concurrency-problems-in-transaction/
https://www.youtube.com/watch?v=sLJ8ypeHGlM
https://brunch.co.kr/@toughrogrammer/17#comments