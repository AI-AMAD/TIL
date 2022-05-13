---
title: "Stack이란??"
date: 2022-05-13
categories: [자료구조]
---
## Stack은 어떤 자료구조인가??

stack은 후입선출 LIFO(Last In First Out)의 자료구조이다. 시간복잡도는 push O(1), pop O(1)이다. 활용 예시는 `후위 표기법 연산`, `괄호 유효성 검사`, `웹 브라우저 방문기록(뒤로가기)`, `깊이 우선탐색(DFS)`이 있다.

![](https://velog.velcdn.com/images/lkdfj6/post/a8e0b3db-dfe3-416e-875f-65c373fc491f/image.png)

> **push & pop**

-   **push**: stack에서 데이터를 추가하는 것을 말한다. stack의 맨 뒤에 데이터를 추가하면 완료되기 때문에 시간복잡도는 O(1)이다.
    
-   **pop**: stack에서 데이터를 추출하는 것을 말한다. push와 동일하게 pop의 경우도 맨 뒤에 데이터를 삭제하면 완료되기 때문에 O(1)의 시간복잡도를 갖는다.
    
-   push, pop 모두 stack의 top에 원소를 추가하거나 삭제하는 형식으로 구현된다