---
title: '영화감독 숌 - 1436'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['브루트 포스']
---

## 문제

666은 종말을 나타내는 숫자라고 한다. 따라서, 많은 블록버스터 영화에서는 666이 들어간 제목을 많이 사용한다. 영화감독 숌은 세상의 종말 이라는 시리즈 영화의 감독이다. 조지 루카스는 스타워즈를 만들 때, 스타워즈 1, 스타워즈 2, 스타워즈 3, 스타워즈 4, 스타워즈 5, 스타워즈 6과 같이 이름을 지었고, 피터 잭슨은 반지의 제왕을 만들 때, 반지의 제왕 1, 반지의 제왕 2, 반지의 제왕 3과 같이 영화 제목을 지었다.

하지만 숌은 자신이 조지 루카스와 피터 잭슨을 뛰어넘는다는 것을 보여주기 위해서 영화 제목을 좀 다르게 만들기로 했다.

종말의 숫자란 어떤 수에 6이 적어도 3개이상 연속으로 들어가는 수를 말한다. 제일 작은 종말의 숫자는 666이고, 그 다음으로 큰 수는 1666, 2666, 3666, .... 과 같다.

따라서, 숌은 첫 번째 영화의 제목은 세상의 종말 666, 두 번째 영화의 제목은 세상의 종말 1666 이렇게 이름을 지을 것이다. 일반화해서 생각하면, N번째 영화의 제목은 세상의 종말 (N번째로 작은 종말의 숫자) 와 같다.

숌이 만든 N번째 영화의 제목에 들어간 숫자를 출력하는 프로그램을 작성하시오. 숌은 이 시리즈를 항상 차례대로 만들고, 다른 영화는 만들지 않는다.

## 입력

첫째 줄에 숫자 N이 주어진다. N은 10,000보다 작거나 같은 자연수이다.

## 출력

첫째 줄에 N번째 영화의 제목에 들어간 수를 출력한다.

## On my way

### for를 이용해서

```swift
import sys

input = sys.stdin.readline()
N = int(input)
deathNum = 665
for _ in range(N):
  deathNum += 1
  for temp in range(deathNum, int(sys.maxsize)):
    if "666" in str(temp):
      deathNum = temp
      break
print(deathNum)
```

💡

---

`sys.maxsize` `sys.maxint` 

9223372036854775807

`sys.float_info.max`
1.7976931348623157e+308

---

### while을 이용해서

```python
import sys

input = sys.stdin.readline()
N = int(input)
deathNum = 665
temp = 665
for _ in range(N):
  deathNum += 1
  while deathNum > 1:
    temp += 1
    if "666" in str(temp):
      deathNum = temp
      break
print(deathNum)
```

💡왜 이렇게 길어지지 했는데 다른 분의 방법을 보니... 아하!

시간 상의 차이는 거의 없다!

## On other way

```python
N = int(input())
movie = 666

while N:
    if "666" in str(movie):
        N -= 1
    movie += 1

print(movie - 1)
```

💡`while N:` 스위프트하다가 파이썬하니까 이런 걸 잊는다...

