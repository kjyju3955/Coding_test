## Coding_test

코딩테스트 준비 겸 알고리즘 공부 겸 파이써닉하게 코드짜는 능력 기르기
 - 하루에 한 문제씩 풀는걸 목표로!
 - 천천히 꾸준하게




### 문제를 풀다가 알게된 것들 + 헷갈렸던 것들 정리
#### itertools
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
  
#### collections
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
  - 그래프에서 두 노드 사이의 최단 경로를 찾고자 할 때 = BFS(너비 우선 탐색)
  - 그래프에서 모든 노드를 방문하고자 할 때 = DFS(깊이 우선 탐색) : BFS보다 조금 더 느림
