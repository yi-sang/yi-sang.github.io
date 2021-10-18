---
title: '오큰수 - 17298'

post-image: ../assets/images/algorithmStudy.jpg

categories: ['Algorithm']

tags: ['스택']


---

# 오큰수

# 문제

크기가 N인 수열 A = A1, A2, ..., AN이 있다. 수열의 각 원소 Ai에 대해서 오큰수 NGE(i)를 구하려고 한다. Ai의 오큰수는 오른쪽에 있으면서 Ai보다 큰 수 중에서 가장 왼쪽에 있는 수를 의미한다. 그러한 수가 없는 경우에 오큰수는 -1이다.

예를 들어, A = [3, 5, 2, 7]인 경우 NGE(1) = 5, NGE(2) = 7, NGE(3) = 7, NGE(4) = -1이다. A = [9, 5, 4, 8]인 경우에는 NGE(1) = -1, NGE(2) = 8, NGE(3) = 8, NGE(4) = -1이다.

## 입력

첫째 줄에 수열 A의 크기 N (1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄에 수열 A의 원소 A1, A2, ..., AN (1 ≤ Ai ≤ 1,000,000)이 주어진다.

## 출력

총 N개의 수 NGE(1), NGE(2), ..., NGE(N)을 공백으로 구분해 출력한다.

## 예제 입력 1 복사

```
4
3 5 2 7
```

## 예제 출력 1 복사

```
5 7 7 -1
```

## 예제 입력 2 복사

```
4
9 5 4 8
```

## 예제 출력 2 복사

```
-1 8 8 -1
```

## On my way

```python
import sys

input = sys.stdin.readline().rstrip
n = int(input())
input = sys.stdin.readline().rstrip
nums = list(map(int, input().split()))
result = [-1] * n
stack = [0]

for i in range(1, n): # i가 n보다 작을 때만
    # 스택에 값이 있고, 스택의 제일 위에 있는 인덱스에 해당하는 값보다 인덱스 i의 값이 크면
    while stack and nums[stack[-1]] < nums[i]:
        result[stack[-1]] = nums[i]
        stack.pop()
    stack.append(i)

print(*result)
```

💡음 전에 풀었던 정답을 참고했다.

하나의 for문 으로 돌리고 stack에 인덱스 역할을 하니까 시간을 절약할 수 있었다.

실제 문제로 나오면 풀 수 있을 까...?

열심히 하자

## Wrong my way

```python
import sys

input = sys.stdin.readline().rstrip
N = int(input())
input = sys.stdin.readline().rstrip().split
NGE = list(map(int, input()))
count = 0
for _ in range(N):
  for value in NGE[count+1:]:
    if NGE[count] < value:
      print(value, end = " ")
      break
  else:
    print(-1, end = " ")
  count += 1
```

💡이중 for문으로 푸니까 시간 초과가 떴다.

