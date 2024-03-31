Created by : seophohoho  
Created datetime : 2024-03-26 10:01  
Tags : #Git #협업  
## 문제 상황
프로젝트를 위해서, A와 B는 각각 `feat/todolist`, `feat/friend` 브랜치에서 작업을 하기로 했습니다. 그런데, B가 `feat/todolist`에 1개의 `commit`을  `push`하게 되었습니다. `feat/todolist`에서 작업하고 있던 A는 그 사실을 모른채로, 본인의 작업물을 `commit`만 하였고, 최종적으로 `push`를 하였습니다. 그러자, 해당 오류를 받게 되었습니다.
```bash
To https://github.com/seophohoho/PlanIsJustNow-be.git
 ! [rejected]        feat/todolist -> feat/todolist (fetch first)
error: failed to push some refs to 'https://github.com/seophohoho/PlanIsJustNow-be.git'
```
## 문제 원인
**`push`하고자 했던 `commit`의 베이스가 원격 저장소의 최신 `commit`과 일치하지 않았습니다.**
## 해결 방법
문제를 해결하기 위해서, B가 최신 `commit` 이력 이전에 A가 원격저장소에 `commit`한 내역이 들어가야 합니다. 이를 위해서 `rebase`를 사용하기로 했습니다.  
A가 `push`한 `commit` 내역들을 `git fetch`를 통해서 최신으로 B의 로컬에 반영하고, 해당 명령어를 통해서 해결했습니다.
```bash
git fetch origin
git rebase <A의 최신 커밋 해시 또는 브랜치 이름>
```
