Created by : seophohoho  
Created datetime : 2023-12-21 16:52  
Tags :  #CS #Algorithm
## INTRO
> [!Question] 이 알고리즘이 좋은 알고리즘인가?

이 궁금증을 해결하기 위해서 해당 알고리즘의 성능을 __'분석'__ 합니다.  
알고리즘의 성능을 분석하기 위해서 다음과 같은 것들을 생각해 볼 수 있습니다.
- 알고리즘을 완수하기 위한 기타 자원 사용량(메모리, 자원장치, 통신).
- 알고리즘의 실행 시간(running time).

위와 같은 것들을 알아내기 위해서 점근적 분석(Asymptotic notation)을 사용합니다.  
## 점근적 분석(Asymptotic Analyze)
점근적 분석이란, 입력되는 데이터의 크기에 따라서 알고리즘의 실행 시간(running time)과 공간(기타 자원)을 얼마나 차지하는가를 식으로 나타내어 측정하는 것을 말합니다.  
하지만 대부분 알고리즘 분석에서 알고리즘의 공간보다는 실행 시간(running time)에 초점을 맞춥니다. 이유는 다음과 같습니다. 
- 주요 관심의 대상자가 시간이기 때문.
- 시간복잡도가 공간복잡도보다 직관적이기 때문.
- 공간보다는 시간이 제한적인 리소스인 경우가 더 많기 때문.

어떤 알고리즘의 실행 시간을 나타내기 위해서 함수식(ex. 4𝑛+100)의 형태로 표현합니다.  
그리고, 알고리즘의 실행 시간에서 중요한 부분인 성장률(rate of growth)만을 나타내기 위해서 중요하지 않은 항과 상수 계수를 제거하여 간단하게 표현합니다.  
> [!Note] 점근(漸近)이란 점점 가까워 지는 모양을 뜻합니다. 점근적 표기법 이라 함은 주어진 함수가 있을 때, 보다 간단한 함수로 만들어 표시함을 뜻합니다.
## 시간복잡도(Time Complexity)
> [!Question] 이 알고리즘의 실행 시간(running time)은 무엇일까? 

여기서 말하는 실행 시간(running time)이란, 알고리즘을 수행하는 데 걸리는 시간을 의미하지 않고, 알고리즘을 수행하는데 필요한 스텝(step) 수를 말합니다.  
왜냐하면, 알고리즘을 실행하는 컴퓨터의 환경마다 걸리는 시간이 달라지기 때문에, 공정한 비교라고 할 수 없습니다. 이러한 이유로 인해서 알고리즘의 계산복잡성은 컴퓨터 성능에 관계없이 machine independent한 방식으로 따져보게 됩니다.  
알고리즘 자체의 효율성은 데이터 개수(𝑛)가 주어졌을 때 덧셈, 뺄셈, 곱셈 등 해당 알고리즘 수행 시 필요한 ‘기본 연산(basic operation)의 횟수’로 표현하는 것이 일반적입니다.  

해당 궁금증을 해결하기 위해서 점근적 분석 안에는 점근적 실행 시간(Asymptotic Running Time)이라는 것이 있습니다.  
점근적 실행 시간(Asymptotic Running Time)이란, 특정 알고리즘의 입력값 𝑛이 무한대를 향할 때(𝑛->∞) 알고리즘의 실행 시간의 추이를 의미합니다. 
그리고 점근적 실행 시간(Asymptotic Running Time)은 달리 말해서, 시간 복잡도(Time Complexity)라고 부릅니다.  
시간복잡도를 표현하기 위해서 '점근적 표기법(Asymptotic Notation)'을 사용합니다.  
점근적 표기법은 크게 3가지가 존재합니다.  
- Big-θ (빅 세타) 표기법
- Big-O (빅 오) 표기법
- Big Ω (빅 오메가) 표기법
## 점근적 표기법_Big-O
알고리즘의 상한선 : 
## 접근적 표기법_Big-θ
알고리즘의 케이스(best,worst,average) 중에서 worst의 경우를 전제로 하여 알고리즘과 비교한다. 
## Reference
- https://ko.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/asymptotic-notation
- https://www.youtube.com/watch?v=tTFoClBZutw
- https://ratsgo.github.io/data%20structure&algorithm/2017/09/13/asymptotic/
- https://nolzaheo.tistory.com/3
