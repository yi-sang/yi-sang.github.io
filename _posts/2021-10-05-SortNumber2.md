---
title: '수 정렬하기 2'

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

💡

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