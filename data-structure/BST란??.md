---
title: "BST란??"
date: 2022-05-20
categories: [자료구조]
---
## 이진탐색트리 BST(Binary Search Tree)란 어떤 자료구조인가??

이진탐색트리는 정렬된 트리이다. 어느 노드를 선택하든 해당 노드의 왼쪽 서브트리에는 그 노드의 값보다 작은 값들을 지닌 노드들로만 이루어져 있고, 노드의 오른쪽 서브트리에는 그 노드의 값보다 큰 값들을 지닌 노드들로만 이루어져 있으며 저장과 동시에 정렬을 하는 자료구조이다.  
검색과 저장, 삭제의 시간복잡도는 모두 O(log n)이고, worst case는 한쪽으로 치우친 트리가 됐을때 O(n)이다.  
![](https://velog.velcdn.com/images/lkdfj6/post/209f4c82-c466-43c3-b49a-7a3c5dad1ced/image.png)

> **이진탐색트리(BST)의 조건**

1.  root node의 값보다 작은 값은 왼쪽 subtree에, 큰 값은 오른쪽 subtree에 있다.
2.  subtree도 1번 조건을 만족한다.(Recursive)

> **이진트리(Binary tree)는 어떤 자료구조 인가?**

모든 node의 child nodes의 갯수가 2 이하인 트리를 이진 트리라고 한다.

> **BST의 worst case 시간복잡도는 O(n)이다. 어떠한 경우에 발생하나??**

다음과 같이 균형이 많이 깨져서 한 쪽으로 치우친 BST의 경우에 worst case가 된다. 이렇게 되면 linked list와 다를게 없어진다. 따라서 탐색시에 O(log n)이 아니라 O(n)이 된다.

![](https://velog.velcdn.com/images/lkdfj6/post/7c2465a1-395d-4afb-882e-57221af1ba3f/image.png)

#### 해결 방법은??

자가 균형 이진 탐색트리(Self-Balancing BST)는 알고리즘으로 이진 트리의 균형이 잘 맞도록 유지하여 높이를 가능한 낮게 유지한다. 대표적으로 AVL트리와 Red-black tree가 있다.  
JAVA에서는 hashmap의 seperate chaning으로써 linked list와 red-black tree를 병행하여 저장한다.