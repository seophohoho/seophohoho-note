Created by : seophohoho
Created time : 2023-12-18 15:29
Tags : #CS 
## INTRO
특정 함수를 실행했을 때, **실행 시간(running time)** 이 어느정도 인지 표현하고 싶다.
> [!NOTE] What is running time?
> 함수/알고리즘 수행에 필요한 스텝(step) 수

표현을 쉽게 하기 위해서 각 코드의 라인 수를 수행하기 위한 필요한 스텝 수는 상수(constant)라고 가정한다. 
```c
int[] test(int[] inputs, int multiplier){
	int[] nums = new int[inputs.length] //cost(step): c1, times: 1
	for(int i=0;i<inputs.length;i++){ //cost(step): c2, times: N+1
		nums[i] = inputs[i] * multiplier; //cost(step): c3, times: N
	}
	return nums; //cost(step): c4, times: 1
}
```
각 코드 라인에 대한 `cost`와 `times`를 곱하고, 모두 더하게 된다면 다음과 같다.
```plaintext
T(N) = c1 + c2 * (N+1) + c3 * N + 1
	= (c2 + c3) * N + c1 + c2 + 1
	= a*N + b
	= θ(N)
```
`a*N + b` 이라는 식이 나오게 되었다. 하지만, 이 식을 통해서 다음과 같은 생각을 할 수 있다.
1. N이 작을 경우에는 실행 시간이 의미가 없다.
2. **그러므로, N->∞ 일 경우에 실행 시간이 궁금하다.**

2번을 생각하기 위해서는 다음과 같은 내용을 생각할 수 있다.
- N이 커질수록 덜 중요한 것은 제거함.
- 최고차항만 의미 있음.
- 최고차항의 계수는 의미 없음.
즉, 해당 조건들을 모두 충족하는 실행 시간(running time) 분석 방법을 점근적 분석(Asymptotic analysis)라고 한다.
> [!NOTE] What is Asymptotic analysis?
> 임의의 함수가 N->∞ 일 경우에, 어떤 함수 형태에 근접해지는지 분석하는 것.
## 시간복잡도(Time complexity)란?
함수/알고리즘의 실행 시간을 표현하는 것인데, 주로 점근적 분석을 통해서 실행 시간을 단순하게 표현하며, 이 때 점근적표기법으로 표현한다.
## 점근적표기법
- Ω(오메가) : 하한(lower bound), 함수 실행 시간은 아무리 빨라도 best 이상이다.
- O(빅 오) : 상한(opper bound), 함수 실행 시간은 아무리 오래 걸려도 worst 정도 이하이다.
- θ(세타) : 평균(tight bound), 상한과 하한이 거의 동일하였을 때 표현(예를 들어서, 각 case 별로 Ω(1), O(1)이라고 가정하였을 때, 해당 case에 대해서 θ(1)이라고 표기할 수 있다.)
## 알고리즘을 분석하는데 따른 case
- best : 최단 시간 실행
- worst : 최장 시간 실행
- average : 일반적인 실행
## Reference
- https://www.youtube.com/watch?v=tTFoClBZutw
- https://m.yes24.com/Goods/Detail/91084402