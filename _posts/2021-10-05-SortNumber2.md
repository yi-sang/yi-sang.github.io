---
title: '수 정렬하기 2 - 2751'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['정렬']
---

# 수 정렬하기 2

# 문제

N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.

## 입력

첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄부터 N개의 줄에는 수가 주어진다. 이 수는 절댓값이 1,000,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.

## 출력

첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.

## 예제 입력 1

```
5
5
4
3
2
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

💡 첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000,000)이 주어진다.
O(1)로 푼다면 1번의 계산이 필요하다.
O(logn)으로 푼다면 20번의 계산이 필요하다.
O(n)으로 푼다면 100만의 계산이 필요하다. 
O(nlogn)으로 푼다면 100만 * 20 = 2000만의 계산이 필요하다.
O(n**2) 로 푼다면 1조의 계산이 필요하다.

파이썬은 1초에 2000만번~5000만번의 계산을 수행할 수 있다.
따라서 적어도 O(nlogn) 시간 복잡도를 이용해야한다.
파이썬 내부함수 정렬(=병합정렬)이나 퀵정렬, 병합정렬, 힙정렬등을 이용하자
메모리가 허용된다면 되도록 Python 3보다는 PyPy 3를 선택하여 코드를 제출하자!
## On other way

```python
import sys
n = int(input())
l = []
for i in range(n):
    l.append(int(sys.stdin.readline()))
for i in sorted(l):
    sys.stdout.write(str(i)+'\n')
```

💡`sys.stdout.write(str(i)+'\n')`