---
title: "array"
date: 2022-05-10
categories: [자료구조]
---
## array란?

-   array는 연관된 data를 메모리상에 연속적이며 순차적으로 미리 할당된 크기만큼 저장하는 자료구조이다.

**array의 특징**

-   고정된 저장 공간
-   순차적인 데이터 저장

**array의 장점**

-   lookup과 append가 빠르다. 따라서 조회를 자주 해야되는 작업에서 array자료구조를 많이 쓴다.

**array의 단점**

-   fixed-size의 특성상 선언시에 array의 크기를 미리 정해야 하므로 메모리의 낭비나  
    추가적인overhead가 발생할 수 있다.

> 만약 미리 예상한 것보다 더 많은 수의 data를 저장하느라  
> array의 size를 넘어서게 된다면??

기존의 size보다 더 큰 array를 선언하여 데이터를 옮겨 할당한다.  
모든 데이터를 옮겼다면 기존 array는 메모리에서 삭제한다.  
이런식으로 동적으로 배열의 크기를 조절하는 자료구조를 dynamic array라고 한다.

## dynamic array란?

-   dynamic array는 size를 자동적으로 resizing하는 array이다.  
    기존에 고정된 size를 가진 static array의 한계점을 보완하고자 고안되었다.  
    dynamic array는 data를 계속 추가하다가 기존에 할당된 memory를 초과하게 되면,  
    size를 늘린 배열을 선언하고 그곳으로 모든 데이터를 옮김으로써 늘어난 크기의 size를 가진 배열이 된다.  
    이를 resize라고 한다. 따라서 dynamic array는 size를 미리 고민할 필요가 없다는 장점이 있다.

> resize란?

![](https://velog.velcdn.com/images/lkdfj6/post/230ba35b-bf2e-475c-a20d-1580102187d2/image.png)

resize의 대표적인 방법으로 doubling이 있다.  
데이터를 추가(append O(1))하다가 메모리를 초과하게 되면 기존 배열의 size보다 두배 큰 배열을 선언하고,  
데이터를 일일이 옮기는 (n개의 데이터를 일일이 옮겨야 하므로 O(n)) 것을 말한다.  
\*\*dynamic array의 단점\*\* - resize를 해야할 때, 예상치 못하게 현저히 낮은 퍼포먼스가 발생한다. - resize에 시간이 많이걸리므로 필요한 것 이상의 memory 공간을 할당받기때문에,  
사용되지 못하고 낭비되는 메모리 공간이 발생한다.

## linked list 란?

![](https://velog.velcdn.com/images/lkdfj6/post/4a9892e6-57d5-4245-b5b3-98e0ca9dc894/image.png)

-   linked list는 Node라는 구조체로 이루어져 있는데, Node는 데이터 값과 다음 Node의  
    address를 저장한다. 물리적인 메모리상에서는 비연속적으로 저장되지만, linked list를 구성  
    하는 각각의 Node가 다음 Node의 address를 가리킴으로써 논리적인 연속성을 가진 자료구조이다.

> 논리적 연속성이란?

각 Node들은 next address 정보를 가지고 있기 때문에 논리적으로 연속성을 유지하면서 연결되어 있다.  
array의 경우 연속성을 유지하기 위해 물리적 메모리 상에서 순차적으로 저장하는 방법을 사용하였고,  
linked list에는 메모리에서 연속성을 유지하지 않아도 되기 떄문에 메모리 사용이 좀더 자유로운 대신,  
next address를 추가적으로 저장해야 하기 때문에 데이터 하나당 차지하는 메모리는 더 커지게 된다.

> 데이터 삽입/삭제

array의 경우 중간에 데이터를 삽입/삭제하게 되면 해당 인덱스의 뒤에 있는 모든 원소들을 옮겨야 했지만  
(그러다 보니 O(n)의 시간복잡도를 갖게 되었다.) 하지만 linked list는 물리적으로 옮길 필요없이  
next address가 가리키는 주소값만 변경하면 되기 때문에 O(1)의 시간복잡도로 삽입/삭제가 가능하다.

**linked list의 장점**

-   데이터가 추가되는 시점에서 메모리를 할당하기 때문에 메모리를 좀더 효율적으로 사용 가능하다.

> array와 linked list의 차이점

array는 메모리 상에서 연속적으로 데이터를 저장하는 자료구조이고  
linked list는 메모리상에서는 연속적이지 않지만, 각각의 원소가 다음 원소의 메모리 주소값을  
저장해 놓음으로써 논리적 연속성을 유지하는 자료구조이다.

그래서 각 시간복잡도가 다르다.

데이터 조회시 array의 경우 O(1), linked list는 O(n)의 시간복잡다를 갖는다.  
삽입/삭제는 array는 O(n) linked list는 O(1)의 시간복잡도를 갖는다.

따라서 얼마만큼의 데이터를 저장 할지 미리 알고있고, 조회를 많이 한다면 array를 사용하는것이 효율적이고  
반면에 몇개의 데이터를 저장 할지 불확실하고 삽입,삭제가 잦다면 linked list를 사용하는것이 효율적이다.