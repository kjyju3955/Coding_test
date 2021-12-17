## 파이썬 공부
#### 1. list 문자 입력 종류
  - append(x) : x를 list의 맨 끝에 추가, iterable이라도 전체를 하나의 객체로 인식해서 추가
  ``` python
  num1 = [1,2,3]
  num1.append(4) # result : num1 = [1,2,3,4]
  
  num2 = [1,2,3]
  num2.append([4,5]) # result : num2 = [1,2,3,[4,5]]
  ```
  - extend(iterable) : iterable의 각 요소를 list 끝에 추가, iterable자료형만 추가 가능
  ``` python
  num1 = [1,2,3]
  num1.extend(4) # error
  num1.extend([4]) # result: num1 = [1,2,3,4]
  
  num2 = [1,2,3]
  num2.extend([4,5,6]) # result : num2 = [1,2,3,4,5,6]
  ```
  - insert(i,x) : i의 위치에 x를 추가, append와 마찬가지로 iterable을 하나의 객체로 인식
  ``` python
  num1 = [1,2,3]
  num1.insert(1, 4) # result : num1 = [1,4,2,3]
  ```
---

#### 2. itertools
  - combinations(list, 갯수) : 조합을 표현할 때 사용, 한 리스트에서 중복을 허용하지 않고 모든 경우의 수 구해줌 (반환되는 항목 수 : n!/r!/(n-r)!
  ``` python
  from itertools import combinations
  num = [1,2,3]
  print(list(combinations(num, 2)) # num에서 2개의 원소를 사용한 중복되지 않는 모든 경우의 수 출력
  ```
  - permutations : 순열을 표현할 때 사용, 한 리스트에서 중복을 허용하는 모든 경우의 수 구해줌 (반환되는 항목 수 : n!/r!)
  ``` python
  from itertools import permutations
  num = [1,2,3]
  print(list(permutations(num, 2)) # num에서 2개의 원소를 사용한 중복되는 모든 경우의 수 출력
  ```
  - product : 데카르트의 곱, 두 개 이상의 리스트의 모든 조합을 구해줌
  ``` python
  from itertools import product
  num = [(1,-1), (2,-2), (3,-3)]
  print(list(product(*num))) # ex) [(1,2,3),(1,2,-3),(1,-2,3), .....]
  ```
  
#### 3. collections
  - Counter : 딕셔너리 내에서 아이템의 발생 빈도를 카운트해서 저장
  ``` python
  from collections import Counter
  
  example = ['A', 'B', 'B', 'C', 'C', 'D', 'A']
  counter = Counter(example)
  print(counter) # result : {'A':2, 'B':2, 'C':2, 'D':1}
  
  counter.update(['C', 'D'])
  print(counter) # result : {'A':2, 'B':2, 'C':3, 'D':2}
  
  print(list(counter.elements())) # result : ['A', 'A', 'B', 'B', 'C', 'C', 'C', 'D', 'D'] * 이때 순서는 랜덤
  
  print(counter.most_common(2)) # counter 중에서 가장 빈도수가 높은 n개의 요소를 튜플로 반환
                                # result : [('C', 3), ('A', 2)]
  ```

#### 추가 공부
  - 딕셔너리 value기준으로 가장 큰 key 찾기
  ``` python
  exam_dict = {"a":1,"b":5,"c":2,"d":4}
  
  print(max(exam_dict, key=exam_dict.get)) # result : "b"
  ```

---
# 알고리즘 공부
#### 1. 그래프
![캡처](https://user-images.githubusercontent.com/55525705/146533200-d214bc04-5a2c-4742-988c-fcec193e8656.JPG)
  - 정점(vertice) : 노드(node)라고도 하며 데이터가 저장됨 (ex-0,1,2,3)
  - 간선 (edge) : 링크(arcs)라고도 하며 정점간의 관계를 나타냄
  - 인접 정점 : 간선에 의해서 연결된 정점 (ex-0과1은 인접 정점)
  - 단순 경로 : 같은 간선을 지나지 않는 경로
  - 차수(degree) : 무방향 그래프에서 하나의 정점에 인접한 정점의 수 (ex-0의 정점은 3)
  - 진출 차수 : 방향 그래프에서 사용되는 용어로 한 노드에서 외부로 나가는 간선의 수
  - 진입 차수 : 방향 그래프에서 사용되는 용어로 한 노드에서 내부로 들어오는 
<br><br>
  <구현 방법>
  1. 인접 행렬 : 그래프의 노드를 2차원 배열로 생성, 인접 정점이면 1 아니면 0을 대입
