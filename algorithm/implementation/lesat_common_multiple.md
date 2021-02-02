# Least common multiple

> 최소공배수



```python
Arr = list(map(int,list(input().split())))

n = 1
while n%Arr[0] or n%Arr[1] or n%Arr[2]:
    n += 1

print(n)
```

