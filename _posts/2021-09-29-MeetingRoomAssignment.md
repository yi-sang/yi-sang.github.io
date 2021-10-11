---
title: '회의실 배정'

post-image: ../assets/images/algorithmStudy.jpg

categories: ['Algorithm']

tags: ['그리디']

---

# 회의실 배정 

# 문제

한 개의 회의실이 있는데 이를 사용하고자 하는 N개의 회의에 대하여 회의실 사용표를 만들려고 한다. 각 회의 I에 대해 시작시간과 끝나는 시간이 주어져 있고, 각 회의가 겹치지 않게 하면서 회의실을 사용할 수 있는 회의의 최대 개수를 찾아보자. 단, 회의는 한번 시작하면 중간에 중단될 수 없으며 한 회의가 끝나는 것과 동시에 다음 회의가 시작될 수 있다. 회의의 시작시간과 끝나는 시간이 같을 수도 있다. 이 경우에는 시작하자마자 끝나는 것으로 생각하면 된다.

## 입력

첫째 줄에 회의의 수 N(1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N+1 줄까지 각 회의의 정보가 주어지는데 이것은 공백을 사이에 두고 회의의 시작시간과 끝나는 시간이 주어진다. 시작 시간과 끝나는 시간은 231-1보다 작거나 같은 자연수 또는 0이다.

## 출력

첫째 줄에 최대 사용할 수 있는 회의의 최대 개수를 출력한다.

## 예제 입력 1

```
11
1 4
3 5
0 6
5 7
3 8
5 9
6 10
8 11
8 12
2 13
12 14
```

## 예제 출력 1

```
4
```

## 힌트

(1,4), (5,7), (8,11), (12,14) 를 이용할 수 있다.

## On my way

```python
import sys  

input = sys.stdin.readline()
time = []
N = int(input)

# 값을 입력받아 리스트에 넣어준다.
for _ in range(N):
  inputTime = sys.stdin.readline().split()
  beginningTime, endTime = map(int, inputTime)
  time.append([beginningTime, endTime])

# 시작 시간을 기준으로 정렬 후
time = sorted(time, key = lambda x: x[0])
# 끝나는 시간을 기준으로 정렬
time = sorted(time, key = lambda x: x[1])
# 이미 시작시간이 오름차순으로 정렬된 상태이기 때문에 끝나는 시간으로 오름차순을 해주어도 자연히 끝나는 시간이 같을 때에는 시작시간의 오름차순으로 정렬이 되어있다.
# 예)
# (2, 4), (1, 4) 상태에서 바로 끝나는 시간으로 정렬하면
# (2, 4), (1, 4) 가 되지만
# 먼저, 시작 시간을 기준으로 정렬하고 끝나는 시간으로 정렬하게 되면
# (2, 4), (1, 4) -> (1, 4), (2, 4) -> (1, 4), (2, 4)
# 시작 시간의 오름차순으로 정렬이 되어있다.

lastTime = 0
count = 0
for biginTime, endTime in time:
  if biginTime >= lastTime:
    count += 1
    lastTime = endTime

print(count)

```

💡 `time = sorted(time, key = lambda x: x[1])`

x[1]을 기준으로 정렬한다.

## On other way

```python
def solution(InputArr):
    answer = 0
    endTime = 0
    for i in range(len(InputArr)):
        if endTime <= InputArr[i][0]:
            endTime = InputArr[i][1]
            answer += 1
    return answer
 
 
N = int(input())
InputArr = []
 
for i in range(N):
    A, B = map(int, input().split())
    InputArr.append([A, B])
 
InputArr.sort(key=lambda x: (x[1], x[0]))
print(solution(InputArr))
```

💡`InputArr.sort(key=lambda x: (x[1], x[0]))`

첫 번째로 x[1]로 정렬을 하고 다음 x[0]으로 정렬한다.

