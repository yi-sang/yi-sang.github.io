---
title: '회전하는 큐 - 1021'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['큐/덱']
---

# 회전하는 큐

## 문제

지민이는 N개의 원소를 포함하고 있는 양방향 순환 큐를 가지고 있다. 지민이는 이 큐에서 몇 개의 원소를 뽑아내려고 한다.

지민이는 이 큐에서 다음과 같은 3가지 연산을 수행할 수 있다.

1.  첫 번째 원소를 뽑아낸다. 이 연산을 수행하면, 원래 큐의 원소가 a1, ..., ak이었던 것이 a2, ..., ak와 같이 된다.
2.  왼쪽으로 한 칸 이동시킨다. 이 연산을 수행하면, a1, ..., ak가 a2, ..., ak, a1이 된다.
3.  오른쪽으로 한 칸 이동시킨다. 이 연산을 수행하면, a1, ..., ak가 ak, a1, ..., ak-1이 된다.

큐에 처음에 포함되어 있던 수 N이 주어진다. 그리고 지민이가 뽑아내려고 하는 원소의 위치가 주어진다. (이 위치는 가장 처음 큐에서의 위치이다.) 이때, 그 원소를 주어진 순서대로 뽑아내는데 드는 2번, 3번 연산의 최솟값을 출력하는 프로그램을 작성하시오.

## 입력

첫째 줄에 큐의 크기 N과 뽑아내려고 하는 수의 개수 M이 주어진다. N은 50보다 작거나 같은 자연수이고, M은 N보다 작거나 같은 자연수이다. 둘째 줄에는 지민이가 뽑아내려고 하는 수의 위치가 순서대로 주어진다. 위치는 1보다 크거나 같고, N보다 작거나 같은 자연수이다.

## 출력

첫째 줄에 문제의 정답을 출력한다.

## 예제 입력 1 복사

```
10 3
1 2 3
```

## 예제 출력 1 복사

```
0
```

## 예제 입력 2 복사

```
10 3
2 9 5
```

## 예제 출력 2 복사

```
8
```

## 예제 입력 3 복사

```
32 6
27 16 30 11 6 23
```

## 예제 출력 3 복사

```
59
```

## 예제 입력 4 복사

```
10 10
1 6 3 2 7 9 8 4 10 5
```

## 예제 출력 4 복사

```
14
```

## On my way

```python
from collections import deque
N, M = map(int, input().split())
queue = deque()
for i in range(1, N+1):
  queue.append(i)
numLocation = deque(map(int, input().split()))
count = 0
for i in numLocation:
  while True:
    if queue[0] == i:
      queue.popleft()
      break
    else:
      if queue.index(i) > len(queue)/2:
        while queue[0] != i:
          queue.rotate(1)
          count += 1
      else:
        while queue[0] != i:
          queue.rotate(-1)
          count += 1
print(count)
```

💡`if queue.index(i) > len(queue)/2:` 조건식을  생각해준다.

`list.index(n)` 해당하는 값의 인덱스를 구해준다. 사실 이게 생각이 잘 안 났다.

## Wrong my way

```python
from collections import deque

n,m = list(map(int,input().split()))
value = list(map(int,input().split()))

q = deque([i+1 for i in range(n)])
count = 0

for x in value:
    while True:
        if q.index(x) == 0:
            q.popleft() # 1번 로직
            break
                # 위치 0과의 거리 차이로 왼쪽으로 이동할 지 오른쪽으로 이동할 지를 결정
        if q.index(x) - 0 <= len(q) - q.index(x): # 2번 왼쪽으로 이동하기 로직
            q.append(q.popleft())
            count += 1
        else:
            q.appendleft(q.pop()) # 3번 오른쪽으로 이동하기 로직
            count += 1
print(count)
```

💡 `q.index(x) - 0 <= len(q) - q.index(x):` 사실 내가 푼 거랑 같은 방식인데 생각의 차이!

