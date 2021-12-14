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
