---
tags: DataStructure
---
# 트리(Tree) 구조

> **노드로 구성된 계층적 자료구조**
> 루트를 만들고, 루트 노드의 child를 추가하고, 그 child에 또 child를 추가하는 방식


![](https://i.imgur.com/p1OFpnY.png)

- **트리** : Node와 Branch를 이용해서, 사이클을 이루지 않도록 구성한 데이터 구조
- **Node** : 트리에서 데이터를 저장하는 기본 요소 (데이터와 다른 연결된 노드에 대한 Branch 정보 포함)
- **Root Node** : 트리 맨 위에 있는 노드
- **Level** : 최상위 노드를 Level 0 으로 하였을 때, 하위 Branch로 연결된 노드의 깊이를 나타냄
- **Parent Node** : 어떤 노드의 다음 레벨에 연결된 노드
- **Child Node** : 어떤 노드의 상위 레벨에 연결된 노드
- **Leaf Node (Terminal Node)** : Child Node가 하나도 없는 노드
- **Sibling (Brother Node)** : 동일한 Parent Node를 가진 노드
- **Depth** : 트리에서 Node가 가질 수 있는 최대 Level


# 이진 트리와 이진 탐색 트리 (Binary Search Tree)


## 이진 트리

> **노드의 최대 Branch가 2인 트리**


## 이진 탐색 트리 (BST)

> **이진 트리에 다음과 같은 추가적인 조건이 있는 트리**
- 왼쪽 노드는 해당 노드보다 작은 값, 오른쪽 노드는 해당 노드보다 큰 값을 가지고 있음
- 주로 데이터 검색(탐색)에 이용됨

![](https://i.imgur.com/Zsie500.png)







>참고
>https://st-lab.tistory.com/300
>https://you88.tistory.com/31