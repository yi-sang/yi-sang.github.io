---
title: '풍선 터뜨리기 - 2346'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['스택']
---
# 풍선 터뜨리기

# 문제
1번부터 N번까지 N개의 풍선이 원형으로 놓여 있고. i번 풍선의 오른쪽에는 i+1번 풍선이 있고, 왼쪽에는 i-1번 풍선이 있다. 단, 1번 풍선의 왼쪽에 N번 풍선이 있고, N번 풍선의 오른쪽에 1번 풍선이 있다. 각 풍선 안에는 종이가 하나 들어있고, 종이에는 -N보다 크거나 같고, N보다 작거나 같은 정수가 하나 적혀있다. 이 풍선들을 다음과 같은 규칙으로 터뜨린다.

우선, 제일 처음에는 1번 풍선을 터뜨린다. 다음에는 풍선 안에 있는 종이를 꺼내어 그 종이에 적혀있는 값만큼 이동하여 다음 풍선을 터뜨린다. 양수가 적혀 있을 경우에는 오른쪽으로, 음수가 적혀 있을 때는 왼쪽으로 이동한다. 이동할 때에는 이미 터진 풍선은 빼고 이동한다.

예를 들어 다섯 개의 풍선 안에 차례로 3, 2, 1, -3, -1이 적혀 있었다고 하자. 이 경우 3이 적혀 있는 1번 풍선, -3이 적혀 있는 4번 풍선, -1이 적혀 있는 5번 풍선, 1이 적혀 있는 3번 풍선, 2가 적혀 있는 2번 풍선의 순서대로 터지게 된다.

## 입력
첫째 줄에 자연수 N(1 ≤ N ≤ 1,000)이 주어진다. 다음 줄에는 차례로 각 풍선 안의 종이에 적혀 있는 수가 주어진다. 종이에 0은 적혀있지 않다.

## 출력
첫째 줄에 터진 풍선의 번호를 차례로 나열한다.

## 예제 입력 1
5
3 2 1 -3 -1

## 예제 출력 1
1 4 5 3 2

## On my way
```swift
import Foundation

var N = Int(readLine()!)!
var ansArray: [Int] = []
var array = readLine()!.split(separator: " ").map { Int($0)! }
var value: Int
var seqArray: [Int] = []
var flag = 0

for i in 1...N {
    seqArray.append(i)
}

while (!array.isEmpty) {
    if (flag == 1) {
        value = array.removeLast()
        ansArray.append(seqArray.removeLast())
    } else {
        value = array.removeFirst()
        ansArray.append(seqArray.removeFirst())
    }
    if (!array.isEmpty) {
        checkDirection(value: value)
    }
}

for i in 0..<ansArray.count {
    print(ansArray[i], terminator: " ")
}

func checkDirection(value: Int) {
    if (value > 0) {
        flag = 0
        rotLeft(value: value)
    } else {
        flag = 1
        rotRight(value: -value)
    }
}

func rotLeft(value: Int) {
    var n = 1
    
    while (n < value) {
        array.append(array.removeFirst())
        seqArray.append(seqArray.removeFirst())
        n += 1
    }
}

func rotRight(value: Int) {
    var n = 1
    
    array.reverse()
    seqArray.reverse()
    while (n < value) {
        array.append(array.removeFirst())
        seqArray.append(seqArray.removeFirst())
        n += 1
    }
    array.reverse()
    seqArray.reverse()
}

```
💡 insert를 사용했으면 reverse() 없이 사용할 수 있어 좀 더 깔끔했을 것 같다.

`array.insert(array.removeLast(), at: 0)`

💡 나는 배열을 두개 사용했는데 클래스를 사용하는 것도 깔끔해보이긴 하는데 코테에서는 튜플을 이용하는 것이 좋을 것 같다.
```swift
class Ballon {
    var index: Int
    var value: Int

    init(_ index: Int, _ value: Int) {
        self.index = index
        self.value = value
    }
}
```

```swift
var tuple : ([Int], [Int]) = (array, seqArray)
print("array: \(tuple.0), seqArray: \(tuple.1)")

// 이름도 붙일 수 있다!
var namedTuple : (array: [Int], seqArray: [Int]) = (array, seqArray)
print("array: \(namedTuple.array), seqArray: \(namedTuple.seqArray)")
```

처음 스위프트를 이용해서 문제를 풀었는데 확실히 파이썬에 비해서 코드가 길다. rot함수면 다 됐던 문제!!
하지만 재밌다..!