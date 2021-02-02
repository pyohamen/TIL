> 시간 복잡도가 상당히 준다.

> 최적화 문제를 결정문제 ( 예 혹은 아니오 로 답하는 문제 ) 로 바꾸어 해결하는 파라메트릭 서치유형은 이진탐색을 이용하여 해결 가능
> 주어진 수가 큰 수라면 가장 먼저 이진탐색을 떠올리자

> Mid ( 중간점 ) 이 핵심

> 종료조건은 Start > end 일 때 ! 더 이상 이진탐색은 의미가 없음



### 재귀

```python
def binary_search(array, target, start, end):
    if start > end: # 이것도 마찬가지로 재귀이기 때문에, 재귀해서 들어온 것을 고려하여 처음 조건을 설정해줘야 한다.
        return None
    mid = (start + end) //2 # 중간점의 인덱스

    if array[mid] == target: # 찾은 경우 인덱스 반환
        return mid

    elif array[mid] > target: # 찾고자 하는 갑이 중간보다 작은 경우, 중간점의 왼쪽 확인
        return binary_search(array,target,start,mid-1)

    else:
        return binary_search(array,target,mid+1,end)


n, target = list(map(int,input().split()))
array = list(map(int,input().split()))

rst = binary_search(array,target,0,n-1)

if rst == None:
    print('원소가 존재하지 않습니다.')

else:
    print(rst + 1)
```

### 반복문

```python
def binary_search(array,target,start,end):
    while start <= end:
        mid = (start + end) // 2

        if array[mid] == target:
            return mid

        elif array[mid] > target:
            end = mid -1

        else:
            start = mid + 1

    return None

n, target = list(map(int,input().split()))

array = list(map(int,input().split()))

rst = binary_search(array,target,0,n-1)

if rst == None:
    print('원소가 존재하지 않습니다.')

else:
    print(rst + 1)
```

