---
title: '좌표 정렬하기 - 11650'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['정렬']
---

# 좌표 정렬하기

# 문제

2차원 평면 위의 점 N개가 주어진다. 좌표를 x좌표가 증가하는 순으로, x좌표가 같으면 y좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.

## 입력

첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000) 좌표는 항상 정수이고, 위치가 같은 두 점은 없다.

## 출력

첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.

## 예제 입력 1

```
5
3 4
1 1
1 -1
2 2
3 3
```

## 예제 출력 1

```
1 -1
1 1
2 2
3 3
3 4
```

## On my way

```python
import sys

input = sys.stdin.readline().strip
N = int(input())
scale = []

for _ in range(N):
  input = sys.stdin.readline().strip().split
  scale.append(list(map(int, input())))
scale.sort(key=lambda x: (x[0], x[1]))
for x, y in scale:
  print(x, y)


```

💡

`scale.append(input())VS scale.append(list(map(int, input())))`

문자열로 정렬하면 101과 11일때 11이 더 크게 정렬된다.

`scale.sort(key=lambda x: (x[0], x[1]))`

x축을 먼저 정렬한 후, y축을 정렬한다.

`scale = sorted(scale, key = lambda x: (x[0], x[1]))`

이런 식으로도 가능!

`for x, y in scale:`

​	`print(x, y)`

## On other way

```python
N = int(input())

nums = []
for i in range(N):
    [a, b] = map(int, input().split())
    nums.append([a, b])
    
nums = sorted(nums)

for i in range(N):
    print(nums[i][0], nums[i][1])
```

💡이게 되네.. 파이썬의 sort는 순차적으로 정렬된 값을 리턴한다.

