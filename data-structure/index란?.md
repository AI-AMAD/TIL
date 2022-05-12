---
title: "인덱스"
date: 2022-05-10
categories: [자료구조]
---
## index란??
-   index는 데이터베이스에서 table의 검색 성능을 높여주는 자료구조를 말한다.
-   일반적인 RDBMS에서는 B+Tree 구조로 된 index를 사용하여 검색속도를 향상 시킨다.
-   책마다 마지막 페이지에 있는 색인과 같은 역할을 하는 자료구조이다.
-   책에서 어떤 용어나 단어를 찾기 위해 첫 페이지부터 끝까지 전체를 훑지 않아도(Full table scan) index를 찾아보면 몇 페이지에 적혀 있는지 바로 찾을 수 있는 것과 비슷한 개념이다.

> **index 구조**

index는 `Btree`, `B+tree`, `Hash`, `Bitmap`으로 구현될 수 있다.  
많은 데이터베이스 시스템에서 index는 B+tree구조를 가진다. index를 생성하게 되면 특정 column(속성, attribute)의 값을 기준으로 정렬하여 데이터의 물리적 위치와 함께 별도파일에 저장한다.

이 때, index에 저장되는 속성값을 search-key값이라고 하고 실제 데이터의 물리적 위치를 저장한 값을 pointer라고 한다. 즉, index는 순서대로 정렬된 search-key값과 pointer값만 저장하기 때문에 table보다 적은 공간을 차지한다.

> **index를 사용하는 이유**

table에 데이터를 지속적으로 저장하게 되면 내부적으로 순서 없이 쌓이게 된다. 이 경우에 특정 조건을 만족하는 데이터를 찾고자 WHERE절을 사용한다면 table의 row(record)를 처음부터 끝까지 모두 접근하여 검색조건과 일치하는지 비교하는 과정이 필요하다. (이를 full table scan이라고 한다.)

하지만 특정 column에 대한 index를 생성해 놓은 경우 해당 속성에 대하여 search-key가 정렬되어 저장되어 있기 때문에 조건 검색(SELECT ~ WHERE)속도가 굉장히 빠르다.

> **클러스터형 인덱스와 보조 인덱스**

#### 클러스터형 인덱스

-   특정 column을 primary key로 지정하면 자동으로 클러스터형 인덱스가 생성되고, 해당 column 기준으로 정렬이 된다. table 자체가 정렬된 하나의 index인 것이다.  
    ![](https://velog.velcdn.com/images/lkdfj6/post/31ea79a2-eb2e-4b06-b4f0-ae21f7a53f5c/image.png)

#### 보조 인덱스(secondary index)

-   일반 책의 찾아보기와 같이 별도의 공간에 인덱스가 생성된다.  
    `create index` 와 같이 index를 생성하거나 고유키(unique key)로 지정하면 보조 인덱스가 생성된다.  
    ![](https://velog.velcdn.com/images/lkdfj6/post/82be9a19-ec8f-448c-b947-a97526bcd703/image.png)

  

> **index의 단점**

**1\. 추가 저장공간 필요**

index를 생성하면 index 자료구조를 위한 저장 공간이 추가적으로 필요하다. 보통 table크기의 10%정도의 공간을 차지한다.

**2\. 느린 데이터 변경 작업**

검색이 아닌 데이터를 변경 할 때, `INSERT`, `UPDATE`, `DELETE`가 자주 발생하면 성능이 나빠질 수 있다. 그 이유는 보통 B+tree구조의 index는 데이터가 추가 삭제 될 때마다 tree의 구조가 변경될 수 있기 때문이다. 즉, 인덱스의 재구성이 필요하기 떄문에 추가적인 자원이 소모된다.

> **index를 효과적으로 사용하는 방법**

-   SELECT WHERE절에 자주 사용되는 column에 대해 index 생성
-   데이터 수정 빈도가 낮을 수록 적합 I/U/D 작업 시, 데이터에 변화가 생기기 때문에 index에서는 매번 정렬을 다시해야하므로 이에 따른 부하 발생
-   데이터의 중복이 높은 column은 index의 효과가 별로 없다. 예를 들어 성별은 종류가 2가지 밖에 없으므로 index를 생성하지 않는 것이 좋다. 즉, 선택도가 낮을때 유리
-   데이터의 양이 많을 수록 성능향상이 크다. 데이터의 양이 적다면 index의 효과보다는 손해가 더 클 수 있다.
-   join조건으로 자주 사용되는 column의 경우
-   한 table에 index가 너무 많으면 데이터 수정시 소요되는 시간이 너무 길어질 수 있다. (한 table당 4~5개 정도 권장)