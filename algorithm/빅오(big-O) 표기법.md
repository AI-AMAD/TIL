---
title: "빅오(big-O)표기법"
date: 2022-05-14
categories: [알고리즘]
---

## 빅오 표기법이란??

컴퓨터과학에서 빅오는 입력값이 커질 때 알고리즘의 실행 시간(시간 복잡도)과 함께 공간 요구사항(공간 복잡도)이 어떻게 증가하는지를 분류하는데 사용되며, 알고리즘의 효율성을 분석하는 데에 유용하게 활용되는 표기법을 말한다.  
점근적 실행 시간을 표기할 때에도 가장 널리 쓰이는 수학적 표기법 중 하나이다. 점근적 실행 시간이란 입력값 n이 커질 때, 즉 입력값이 무한대를 향할 때 lim함수의 실행 시간의 추이를 의미한다.

그리고 이 점근적 실행 시간을 달리 말하면 시간 복잡도라고 할 수 있다. 시간 복잡도의 사전적 정의는 어떤 알고리즘을 수행하는 데 걸리는 시간을 설명하는 계산 복잡도를 의미하며 계산 복잡도를 표기하는 대표적인 방법이 바로 빅오다.

빅오로 시간 복잡도를 표현할 때는 최고차항만을 표기하며, 계수는 무시한다. 예를 들어 입력값 n에 대해 4n^2+3n+4 번 만큼 계산하는 함수가 있다면 이 함수의 시간 복잡도는 최고차항인 4n^2만을 고려한다. 이 중에서도 계수는 무시하며 n^2만을 고려한다. 즉 여기서의 시간복잡도는 O(n^2)이 된다.

이처럼 시간 복잡도를 표기할 때는 입력값에 따른 알고리즘의 실행 시간의 추이만을 살피게 되고 이 추이에 따른 빅오 표기법의 종류는 크게 다음과 같다.

**O(1)**: 입력값이 아무리 커도 실행 시간은 일정하다. 최고의 알고리즘이라 할 수 있지만 상수 값이 상상을 넘어설 정도로 매우 크다면 사실상 일정한 시간의 의미가 없다. 그러므로 최고의 알고리즘이 될 수 있지만 그만큼 신중해야 한다.

**O(log n)**: 로그는 매우 큰 입력값에도 크게 영향을 받지 않는 편으로 웬만한 n의 크기에 대해서도 매우 견고한 알고리즘이다. 대표적으로 `이진 검색`이 이에 해당한다.

**O(n)**: 입력값만큼 실행 시간에 영향을 받으며, 알고리즘을 수행하는 데 걸리는 시간은 입력값에 비례한다. 이러한 알고리즘을 `선형 시간 알고리즘`이라고 한다. 정렬되지 않은 리스트에서 최댓값 또는 최솟값을 찾는 경우가 이에 해당하며 이 값을 찾기 위해서는 모든 입력값을 적어도 한 번 이상은 살펴봐야 한다.

**O(n log n)**: 병합 정렬을 비롯한 대부분의 효율 좋은 정렬 알고리즘이 이에 해당한다. 적어도 모든 수에 대해 한 번 이상은 비교해야 하는 비교 기반 정렬 알고리즘은 아무리 좋은 알고리즘도 O(n log n)보다 빠를 수 없다.

**O(n^2)**: 버블정렬 같은 비효율적인 정렬 알고리즘이 이에 해당한다.

**O(2^n)**: 피보나치 수를 재귀로 계산하는 알고리즘이 이에 해당한다. 간혹 n^2와 혼동하는 경우가 있는데 처음에는 비슷해 보이지만 2^n이 훨씬 더 크다.

**O(n!)**: 가장 느린 알고리즘으로, 입력값이 조금만 커져도 웬만한 다항시간 내에는 계산이 어렵다.

이를 알고리즘의 풀이 시간 순으로 나열하면 다음과 같다.

> **O(1) < O(log n) < O(n) < O(n log n) < O(n^2) < O(2^n) < O(n!)**  
> `O(1)이 가장 빠르고 O(n!)로 갈수록 느려진다.`

빅오 표기법은 시간 복잡도 외에도 `공간 복잡도`를 표현하는 데에도 널리 쓰인다. 또한 알고리즘은 흔히 '시간과 공간이 트레이드오프' 관계다. 실행 시간이 빠른 알고리즘은 공간을 많이 사용하고, 공간을 적게 차지하는 알고리즘은 실행 시간이 느리다는 말이다.

> **상한 & 최악**

빅오(O)는 상한을 의미한다. 이외에 하한을 나타내는 빅오메가, 평균을 의미하는 빅세타가 있는데

여기서 중요한 포인트는 상한 = 최악의 경우 와 혼동하는 것이다.

빅오 표기법은 정확하게 쓰기에는 너무 길고 복잡한 함수를 "적당히 정확하게" 표현하는 방법일 뿐,

최악의 경우/ 평균적인 경우의 시간 복잡도와는 아무런 관계가 없는 개념이다.

빅오 표기는 복잡하 함수 f(n)이 있을 경우 이 함수의 실행 상한과 하한을 의미힌다.

즉, 가장 빨리 실행될때가 하한, 가장 늦게 실행될때가 상한을 뜻한다.

이 중 가장 늦게 실행될 때를 빅오(O), 가장 빨리 실행될 때를 빅오메가(Ω), 평균을 빅세타(θ) 로 지칭한다.

n이 작을때, 즉 n0 이하 일때의 값이 작은 경우는 무시하며 빅오 표기법은 n이 매우 클 때의 전체적인 큰 그림에 집중한다.