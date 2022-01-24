---
title: '성 지키기 - 1236'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['탐색']
---
# 성 지키기 
# 문제
영식이는 직사각형 모양의 성을 가지고 있다. 성의 1층은 몇 명의 경비원에 의해서 보호되고 있다. 영식이는 모든 행과 모든 열에 한 명 이상의 경비원이 있으면 좋겠다고 생각했다.

성의 크기와 경비원이 어디있는지 주어졌을 때, 몇 명의 경비원을 최소로 추가해야 영식이를 만족시키는지 구하는 프로그램을 작성하시오.

## 입력
첫째 줄에 성의 세로 크기 N과 가로 크기 M이 주어진다. N과 M은 50보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에는 성의 상태가 주어진다. 성의 상태는 .은 빈칸, X는 경비원이 있는 칸이다.

## 출력
첫째 줄에 추가해야 하는 경비원의 최솟값을 출력한다.

## 예제 입력 1
4 4
....
....
....
....
## 예제 출력 1
4
## 예제 입력 2
3 5
XX...
.XX..
...XX
## 예제 출력 2
0
## 예제 입력 3
5 8
....XXXX
........
XX.X.XX.
........
........
## 예제 출력 3
3

## On my way

```python
N, M = map(int, input().split())
array = []
colCnt = 0
rowCnt = 0

for i in range(N):
    data = input()
    array.append(data)

rotArray = ["" for i in range(M)]

for i in range(N):
    if 'X' not in array[i]:
        colCnt += 1
    for j in range(M):
        rotArray[j] += array[i][j]
for i in range(M):
    if 'X' not in rotArray[i]:
        rowCnt += 1
print(max(rowCnt, colCnt))
```
💡 rotated Array를 만들어두고 똑같이 비교했다.
max(행별로 필요한 경비원의 인원, 열별로 필요한 경비원의 인원)

## On other way

```python
N, M = map(int, input().split())
array = []
for _ in range(n):
    array.append(input())

row = [0]*n
column = [0]*m

for i in range(n):
    for j in range(m):
        if array[i][j] == 'X':
            row[i] = 1
            column[j] = 1
row_count = 0
for i in range(n):
    if row[i] == 0:
        row_count += 1
column_count = 0
for j in range(m):
    if column[j] == 0:
        column_count += 1
print(max(row_count, column_count))
```
💡 각 행 열 별로 [0, 0,..]로 된 리스트를 생성해두고 경비원이 필요한 행 열이라면 1로 바꿔주는 로직이다.