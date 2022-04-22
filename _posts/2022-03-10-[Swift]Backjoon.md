---
title: '백준 문제 풀이'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# 백준 문제 풀이

## 서론

풀어보니 스위프트만의 매력이 있는 것 같다. 사용할 수 있는 메소드가 있다면 최대한 사용해보려고 한다. 시간 단축에 큰 힘이 될 것 같다. `import foundation`은 필요할 때와 불 필요할 때를 구분짓고 싶지만 사실 1분 1초가 급한 상황에서 그게 무슨 의미가 있을까 싶어 그냥 무조건 쓰기로 했다.

[문제 모음](https://github.com/tony9402/baekjoon)을 활용하여 문제 순서를 정하였다. 원래 페이지 하나에 문제 하나씩 했다면 이제는 한 페이지에 모두 정리하려한다.
다른 사람이 찾기에는 이전 방법이 좋겠지만 게시글 작성만 하고 다시 찾아보지 않는 나를 보며 한 페이지에 정리하기로 했다.
문자열부터 시작하여 꾸준히 풀어봐야겠다.

# 1. 문자열

|          순번          |        문제 번호         |        문제 이름         |         난이도          |        풀이 링크         |
| :-----: | :-----: | :-----: | :-----: | :-----: |
| 00 | <a href="https://www.acmicpc.net/problem/3029" target="_blank">3029</a> | <a href="https://www.acmicpc.net/problem/3029" target="_blank">경고</a> | <img height="25px" width="25px" src="https://static.solved.ac/tier_small/3.svg"/> |  [경고](#경고---3029) |
| 01 | <a href="https://www.acmicpc.net/problem/11720" target="_blank">11720</a> | <a href="https://www.acmicpc.net/problem/11720" target="_blank">숫자의 합</a> | <img height="25px" width="25px" src="https://static.solved.ac/tier_small/4.svg"/> | [숫자의 합](#숫자의-합---11720)|
| 02 | <a href="https://www.acmicpc.net/problem/11365" target="_blank">11365</a> | <a href="https://www.acmicpc.net/problem/11365" target="_blank">!밀비 급일</a> | ![링크](https://static.solved.ac/tier_small/4.svg) | [!밀비 급일](#밀비-급일---11365) |
| 03 | <a href="https://www.acmicpc.net/problem/9046" target="_blank">9046</a> | <a href="https://www.acmicpc.net/problem/9046" target="_blank">복호화</a> | <img height="25px" width="25px" src="https://static.solved.ac/tier_small/5.svg"/> | [복호화](#복호화---9046) |
| 04 | <a href="https://www.acmicpc.net/problem/10798" target="_blank">10798</a> | <a href="https://www.acmicpc.net/problem/10798" target="_blank">세로읽기</a> | <img height="25px" width="25px" src="https://static.solved.ac/tier_small/5.svg"/> | [세로읽기](#세로읽기---10798) |
| 05 | <a href="https://www.acmicpc.net/problem/20154" target="_blank">20154</a> | <a href="https://www.acmicpc.net/problem/20154" target="_blank">이 구역의 승자는 누구야?!</a> | <img height="25px" width="25px" src="https://static.solved.ac/tier_small/5.svg"/> | [이 구역의 승자는 누구야?!](#이-구역의-승자는-누구야---20154)|

## 경고 - 3029
```swift
import Foundation

let input1 = readLine()!.split(separator: ":").map{ Int($0)! }
let input2 = readLine()!.split(separator: ":").map{ Int($0)! }
var t1 = input1[0]*3600 + input1[1]*60 + input1[2]
var t2 = input2[0]*3600 + input2[1]*60 + input2[2]
let t = t1 > t2  ? t2 + 24*3600 - t1 : t2 - t1
let h = t / 60 / 60
let m = t / 60 % 60
let s = t % 60
var ary = [h, m, s]
// 정인이는 적어도 1초를 기다리며, 많아야 24시간을 기다린다.
if h == 0 && m == 0 && s == 0 {
    print("24:00:00")
} else {
    print(ary.map{ String(format: "%02d", $0) }.joined(separator: ":"))
}
```
## 숫자의 합 - 11720
```swift
import Foundation

let n = Int(readLine()!)
// Int 타입은 Character 타입에 대한 변환용 이니셜라이저가 없으므로 String 타입으로 변환한 후 사용한다.
let intInput = Array(readLine()!).map { Int(String($0))! }
print(intInput.reduce(0, +))
```
## !밀비 급일 - 11365
```swift
import Foundation

while let reverseInput = readLine() {
    if reverseInput == "END" {
        break
    }
    print(String(reverseInput.reversed()))
}
```
## 복호화 - 9046
### 방법1 - C 처럼 풀기
```swift
import Foundation

let n = Int(readLine()!)!
for _ in 0..<n {
    let input = readLine()!
    var replaceString = ""
    input.forEach {
        if $0 == " " {
            return
        }
        replaceString += String($0)
    }
    var maxCnt: Int = 0
    var answerLetter = " "
    var letterDict: [String: Int] = [:]
    for val in replaceString {
        letterDict[String(val), default: 0] += 1
    }
    for (i, c) in letterDict {
        if c == letterDict.values.max() {
            maxCnt += 1
            answerLetter = String(i)
        }
    }
    if maxCnt > 1 {
        print("?")
    } else {
        print(answerLetter)
    }
}
```
### 방법 2 - Swift 처럼 풀기
```swift
import Foundation

let n = Int(readLine()!)!
for _ in 0..<n {
    var input = readLine()!
    input = input.replacingOccurrences(of: " ", with: "")
    let letterCount = input.reduce(into: [:]) { counts, letter in
        counts[letter, default: 0] += 1
    }
    var maxCnt: Int = 0
    var answerLetter = " "
    for (i, c) in letterCount {
        if c == letterCount.values.max() {
            maxCnt += 1
            answerLetter = String(i)
        }
    }
    if maxCnt > 1 {
        print("?")
    } else {
        print(answerLetter)
    }
}
```
## 세로읽기 - 10798
```swift
import Foundation

var maxLen = 0
var array: [[Character]] = []
var answer = ""
for _ in 0..<5 {
    let input = readLine()!
    let inputAry = Array(input)
    maxLen = max(inputAry.count, maxLen)
    array.append(inputAry)
}
for i in 0..<maxLen {
    for j in 0..<5 {
        if array[j].count <= i {
            continue
        }
        answer += String(array[j][i])
    }
}
print(answer)
```
## 이 구역의 승자는 누구야?! - 20154
```swift
import Foundation

let dict: [Character:Int] = ["A":3, "B":2, "C":1, "D":2, "E":3, "F":3, "G":3, "H":3, "I":1, "J":1, "K":3, "L":1, "M":3, "N":3, "O":1, "P":2, "Q":2, "R":2, "S":1, "T":2, "U":1, "V":1, "W":2, "X":2, "Y":2, "Z":1]

let input = Array(readLine()!)
var totalSum = 0
for alpha in input {
    totalSum += dict[alpha, default:0]
}
if (totalSum % 10) % 2 == 1 {
    print("I'm a winner!")
} else {
    print("You're the winner?")
}
```