---
title: "Queue란??"
date: 2022-05-12
categories: [자료구조]
---
## Queue는 무슨 자료구조인가??

큐는 선입선출 FIFO(First In First Out)의 자료구조이다. 시간복잡도는 enqueue O(1), dequeue O(1)이다. 활용 예시는 `캐시구현`, `프로세스 관리`, `너비우선탐색(BFS)`가 있다.

![](https://velog.velcdn.com/images/lkdfj6/post/35179e71-7383-4895-8b1c-b19bfc93bfe0/image.png)

> **FIFO**

Queue는 시간 순서상 먼저 집어 넣은 데이터가 먼저 나오는 선입 선출 FIFO형식으로 데이터를 저장하는 자료구조이다.

> **enqueue & dequeue**

큐에서 데이터를 추가하는 것을 enqueue라고 한다.  
큐에서 데이터를 추출 하는 것은 dequeue라고 한다.

euqueue의 경우 큐의 맨 뒤에서 데이터를 추가하면 완료되기 때문에 시간복잡도는 O(1)이고 이와 비슷하게 dequeue의 경우 맨 앞의 데이터를 삭제하면 완료 되기 때문에 동일하게 O(1)의 시간복잡도를 갖는다.

> **구현 방식**

1.  Array-based queue: enqueue와 dequeue 과정에서 남는 메모리가 생긴다. 따라서 메모리의 낭비를 줄이기 위해 주로 Circular queue형식으로 구현을 한다.  
    ![](https://velog.velcdn.com/images/lkdfj6/post/f28b71fb-1231-453f-a813-fcd1af4ec3c3/image.png)

2.List-based: 재할당이나 메모리 낭비의 걱정을 할 필요가 없어진다.

> **Circular queue**

큐의 개념에서 조금 확장한 자료구조들로는 양쪽에서

> **Array-based 와 List-based의 차이**

**Array-based**의 경우 큐는 circular 큐로 구현하는 것이 일반적이다. 이는 메모리를 효율적으로 사용하기 위함이다. 또한 enqueue가 계속 발생하면 fixed size를 넘어서게 되기 때문에, dynamic array와 같은 방법으로 array의 size를 확장시켜야 한다. 그럼에도 enqueue의 시간복잡도는 O(1)을 유지할 수 있다.

**List-based**의 경우 보통 singly-linked list로 구현한다. enqueue는 단순히 singly-linked list에서 append를 하는것으로 구현되고, 이 때 시간복잡도는 O(1)이다. dequeue는 맨 앞의 원소를 삭제하고 first head를 변경하면 되기 때문에 이 연산도 O(1)의 시간이 걸린다.

요약하자면, 두 가지 종류의 자료구조로 큐를 구현하더라도 enqueue와 dequeue는 모두 O(1)의 시간복잡도를 갖는다. Array-base의 경우 전반적으로 performance가 더 좋지만, worst case의 경우에는 훨씬 더 느릴 수 있다(resize). List-base의 경우에는 enqueue를 할 때마다 memory allocation을 해야 하기 때문에 전밪적인 runtime이 느릴 수 있다.