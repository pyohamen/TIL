# 기둥과 보

> https://programmers.co.kr/learn/courses/30/lessons/60061



- 기둥이든 보든, 설치되고 삭제되는 기능만 있기 때문에, 2차원배열상에 표시할 필요없다.
  - 기둥과, 보 정보들을 가진 1차원 리스트를 활용하여 각 정보들의 존재여부 검증은 v in list 로 해주면 된다.
- 차례대로 삭제나 설치 일단 해보고
  - 해당 작업이 불가능 하다면 무르기



- Code

  ```python
  def isPossible(r):
      for y, x, w in r:
          # 보라면
          if w:
              if [y, x - 1, 0] not in r and [y + 1, x - 1, 0] not in r and not ([y - 1, x, 1] in r and [y + 1, x, 1] in r):
                  return True
          # 기둥이라면
          else:
              if x != 0 and [y, x, 1] not in r and [y - 1, x, 1] not in r and [y, x - 1, 0] not in r:
                  return True
  
      return False
  
  
  def solution(n, build_frame):
  
      r = []
  
      i = 1
  
      for y, x, w, t in build_frame:
          i += 1
          s = [y, x, w]
          # 설치
          if t:
              r.append(s)
              if isPossible(r):
                  r.remove(s)
  
          # 삭제이면
          elif t == 0 and s in r:
              r.remove(s)
              if isPossible(r):
                  r.append(s)
  
      r = sorted(r, key=lambda x: (x[0], x[1], x[2]))
  
      return r
  ```

  