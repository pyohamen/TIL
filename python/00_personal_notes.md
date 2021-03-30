# Python Syntax

> APS 공부하다가 그 때 그 때 필요한 문법들 정리
>
> 이후에 Syntax 주피터 노트북들에 모두 있는 \( 아마 거의 ? \) 내용이긴 함

* 소수점 표기

  ```python
  a=float(input())
  print("{:.6f}".format(a))
  ```

* 뒤집기

  ```python
  a=[1,2,3]
  a.reverse()
  print(a)

  => [3,2,1]
  ```

* iterable 을 특정한 문자열로 만들기

  ```python
  print('!'.join(word))   ###join 앞에 연결고리를 기입해줌
  print(' '.join(word))
  ```

* .으로 나뉜 인풋 받고, 원하는 만큼 공백넣기 \( [https://dojang.io/mod/page/view.php?id=2300](https://dojang.io/mod/page/view.php?id=2300) \)

  ```python
  a,b,c = input().split('.')
  print("{:0>4}.{:0>2}.{:0>2}".format(a,b,c))
  ```

* 진수

  ```python
  value = 60

  b = bin(value) = "0b~"
  o = oct(value) = "0o~"
  h = hex(value) = "0x~"

  b = "{:#b}".format(value)
  o = "{:#o}".format(value)
  h = "{:#h}".format(value)

  value = int("0o13",8) = 11
  value = int("0b11",2) = 3
  value = int("0xf",16) = 15
  ```

* 특정한 문자 제거하기

  ```python
  a = oct(int(input())
  # a = '0o12'

  print(a.lstrip('0o')
  ```

* 아스키 코드

  ```python
  print(chr(45))
  print(ord("A"))
  ```

* 비트연산

  ```python
  비트 연산자 (Bitwise Operators):
  a = 60, b = 13 이라 가정한다.

  a = 0011 1100

  b = 0000 1101

  Operator    Description    Example
  &    AND 연산. 둘다 참일때만 만족    (a & b) = 12 → 0000 1100
  |    OR 연산. 둘 중 하나만 참이여도 만족    (a | b) = 61 → 0011 1101
  ^    XOR 연산. 둘 중 하나만 참일 때 만족    (a ^ b) = 49 → 0011 0001
  ~    보수 연산.    (~a) = -61 → 1100 0011
  <<    왼쪽 시프트 연산자. 변수의 값을 왼쪽으로 지정된 비트 수 만큼 이동    a << 2 = 240 → 1111 0000
  >>    오른쪽 시프트 연산자. 변수의 값을 오른쪽으로 지정된 비트 수 만큼 이동    a >> 2 = 15 → 0000 1111
  ```

* 리스트 컴프리 헨션

  ```python
  array = [i for i in range(20) if i % 2 == 1 ]
  array = [i * i for i in range(1,10)]
  ```

* 리스트에서 특정 값의 원소 모두 제거

  ```python
  a = [1,2,3,4,5,5,5]
  remove_set = {3,5}

  result = [i for i in a if not in remove_set]
  print(result)

  [1,2,4]
  ```

