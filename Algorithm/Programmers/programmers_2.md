# 영어끝말잇기

> https://programmers.co.kr/learn/courses/30/lessons/12981



- aps

  ```
  단어 재사용 안됨
  
  탈락발생
      나왔던 단어
      규칙위반
  
  탈락 발생이 몇바퀴째인지 반환
  탈락 발생 인덱스 반
  ---------------
  a([]): 시작하며 쌓이는 단어들
  
  ----------------
  
  words 안에서 하나씩 a에 추가
  for i, w in enumerate(words):
  
      새로 추가할 것이 이미 나왔던 거나 규칙위반이면
      if (w in a) or a[-1][-1] != w[0]
  
          현재 i 를 보고 [추가하던 인덱스, a의 row (몇번째)] 반환
          Return [i % n, (i // n) + 1]
  
      규칙위반 아니면 추가
      a.append(w)
  
  다했으면 [0,0] 반환
  ```

  

- code

  ```python
  def solution(n, words):
  
      a = [words[0][0]]
  
      for i, w in enumerate(words):
          if (w in a) or a[-1][-1] != w[0]:
              return [(i % n) + 1, (i // n) + 1]
  
          a.append(w)
  
      return [0, 0]
  
  
  n = 3
  words = ["tank", "kick", 'know', 'wheel', 'land', 'dream', 'mother', 'robot', 'tank']
  
  print(solution(n, words))
  ```

  