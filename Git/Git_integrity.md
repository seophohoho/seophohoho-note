Created by : seophohoho  
Created datetime : 2023-12-22 12:06  
Tags :  #Git 
## Git 무결성
- Git은 데이터를 저장하기 전에 checksum을 구하고, 해당 checksum으로 데이터를 관리한다.  
- checksum은 SHA-1 해시를 사용해서 파일의 내용이나 디렉터리 구조를 이용헤서 생성한다.
- 만들어진 checksum의 길이는 40자 16진수 문자열이다.
- Git은 파일의 이름으로 저장하지 않고, 해당 파일의 checksum으로 저장한다.
```text
24b9da6552252987aa493b52f8696cd6d3b00373
```


