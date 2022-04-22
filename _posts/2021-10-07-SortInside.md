---
title: '소트인사이드 - 1427'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['정렬']
---

# 소트인사이드

# 문제

배열을 정렬하는 것은 쉽다. 수가 주어지면, 그 수의 각 자리수를 내림차순으로 정렬해보자.

## 입력

첫째 줄에 정렬하고자하는 수 N이 주어진다. N은 1,000,000,000보다 작거나 같은 자연수이다.

## 출력

첫째 줄에 자리수를 내림차순으로 정렬한 수를 출력한다.

## 예제 입력 1

```
2143
```

## 예제 출력 1

```
4321
```

## On my way

```python
N = input()
output = sorted(N, reverse=True)
print(*output, sep='')
```

💡

## On other way

```swift
let n = Int(readLine()!)!
var numberList: [Int] = []

for _ in 1...n {
    numberList.append(Int(readLine()!)!)
}

numberList.sort()

for i in numberList {
    print(i)
}
```

💡 거의 비슷하다 좀 더 익숙해지고 싶다.
