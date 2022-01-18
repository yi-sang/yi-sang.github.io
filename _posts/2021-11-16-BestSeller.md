---
title: '베스트셀러'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['탐색']
---
# 베스트셀러 
# 문제
김형택은 탑문고의 직원이다. 김형택은 계산대에서 계산을 하는 직원이다. 김형택은 그날 근무가 끝난 후에, 오늘 판매한 책의 제목을 보면서 가장 많이 팔린 책의 제목을 칠판에 써놓는 일도 같이 하고 있다.

오늘 하루 동안 팔린 책의 제목이 입력으로 들어왔을 때, 가장 많이 팔린 책의 제목을 출력하는 프로그램을 작성하시오.

## 입력
첫째 줄에 오늘 하루 동안 팔린 책의 개수 N이 주어진다. 이 값은 1,000보다 작거나 같은 자연수이다. 둘째부터 N개의 줄에 책의 제목이 입력으로 들어온다. 책의 제목의 길이는 50보다 작거나 같고, 알파벳 소문자로만 이루어져 있다.

## 출력
첫째 줄에 가장 많이 팔린 책의 제목을 출력한다. 만약 가장 많이 팔린 책이 여러 개일 경우에는 사전 순으로 가장 앞서는 제목을 출력한다.

## 예제 입력 1
5
top
top
top
top
kimtop
## 예제 출력 1
top
## 예제 입력 2
9
table
chair
table
table
lamp
door
lamp
table
chair
## 예제 출력 2
table
## 예제 입력 3
6
a
a
a
b
b
b
## 예제 출력 3
a
## 예제 입력 4
8
icecream
peanuts
peanuts
chocolate
candy
chocolate
icecream
apple
## 예제 출력 4
chocolate
## 예제 입력 5
1
soul
## 예제 출력 5
soul


## On my way

```python
from array import array
from ctypes.wintypes import tagMSG
import numbers


N = int(input())
ls = []
dict = {}
for i in range(N):
    data = input()
    ls.append(data)

init = 1
ls.sort()
dict[ls[0]] = init
maxInt = 0
for i in range(1, len(ls)):
    if ls[i-1] == ls[i]:
        init += 1
        dict[ls[i]] = init
        
    else:
        init = 1
        dict[ls[i]] = init
        
target = max(dict.values())
array = []

for book, number in dict.items():
    if number == target:
        array.append(book)
print(sorted(array)[0])

```
💡 counter함수를 쓸 수 있었지만 직접 더 해 보았다.

## On other way
```python
n = int(input())
books = {}
for _ in range(n):
    book = input()
    if book not in books:
        books[book] = 1
    else:
        boos[book] += 1
target = max(books.values())
array = []
for book, number in boos.items():
    if number == target:
        array.append(book)

print(sorted(array)[0])
```
💡 딕셔너리를 사용할 때 `if - not in` 구문이 상당히 편한 것 같다.