---
title: '수 정렬하기 - 2750'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['정렬']
---

# 수 정렬하기

# 문제

N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.

## 입력

첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000)이 주어진다. 둘째 줄부터 N개의 줄에는 수 주어진다. 이 수는 절댓값이 1,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.

## 출력

첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.

## 예제 입력 1

```
5
5
2
3
4
1
```

## 예제 출력 1

```
1
2
3
4
5
```

## On my way

```python
from sys import stdin

input = stdin.readline().strip
N = int(input())
numbers = []
for i in range(N):
  numbers.append(int(stdin.readline().strip()))

numbers.sort()
print(*numbers)
```

💡

## On other way

```python
n = int(input())
array = []

for _ in range(n):
    array.append(int(input()))

# 선택정렬
for i in range(n):
    min_index = i
    for j in range(i + 1, n):
        if array[min_index] > array[j]:  # 가장 작은 수의 인덱스를 찾는다
            min_index = j
    array[i], array[min_index] = array[min_index], array[i]  # 가장 앞에 것과 대체


for i in array:
    print(i)
```

💡선택 정렬

`array[i], array[min_index] = array[min_index], array[i]`