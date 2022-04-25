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
문자열부터 시작하여 꾸준히 풀어봐야겠다.

---

# 1. 문자열
<details>
<summary>문제 목차</summary>
<div markdown="1">

|          순번          |        문제 번호         |        문제 이름         |         난이도          |        풀이 링크        |
| :-----: | :-----: | :-----: | :-----: | :-----: |
| 00 | <a href="https://www.acmicpc.net/problem/3029" target="_blank">3029</a> | <a href="https://www.acmicpc.net/problem/3029" target="_blank">경고</a> | ![](/assets/images/b3.svg){: width="4%" height="4%"} |  [바로가기](#경고---3029) |
| 01 | <a href="https://www.acmicpc.net/problem/11720" target="_blank">11720</a> | <a href="https://www.acmicpc.net/problem/11720" target="_blank">숫자의 합</a> | ![](/assets/images/b2.svg){: width="4%" height="4%"} | [바로가기](#숫자의-합---11720)|
| 02 | <a href="https://www.acmicpc.net/problem/11365" target="_blank">11365</a> | <a href="https://www.acmicpc.net/problem/11365" target="_blank">!밀비 급일</a> | ![](/assets/images/b2.svg){: width="4%" height="4%"} | [바로가기](#밀비-급일---11365) |
| 03 | <a href="https://www.acmicpc.net/problem/9046" target="_blank">9046</a> | <a href="https://www.acmicpc.net/problem/9046" target="_blank">복호화</a> | ![](/assets/images/b1.svg){: width="4%" height="4%"} | [바로가기](#복호화---9046) |
| 04 | <a href="https://www.acmicpc.net/problem/10798" target="_blank">10798</a> | <a href="https://www.acmicpc.net/problem/10798" target="_blank">세로읽기</a> | ![](/assets/images/b1.svg){: width="4%" height="4%"} | [바로가기](#세로읽기---10798) |
| 05 | <a href="https://www.acmicpc.net/problem/20154" target="_blank">20154</a> | <a href="https://www.acmicpc.net/problem/20154" target="_blank">이 구역의 승자는 누구야?!</a> | ![](/assets/images/b1.svg){: width="4%" height="4%"} | [바로가기](#이-구역의-승자는-누구야---20154)|

</div>
</details>

# 2. 이분 탐색
<details>
<summary>문제 목차</summary>
<div markdown="1">

|          순번          |         문제 번호         |        문제 이름         |         난이도          |        풀이 링크         |
| :-----: | :-----: | :-----: | :-----: | :-----: |
| 00 | <a href="https://www.acmicpc.net/problem/1789" target="_blank">1789</a> | <a href="https://www.acmicpc.net/problem/1789" target="_blank">수들의 합</a> | ![](/assets/images/s5.svg){: width="4%" height="4%"} | [바로가기](#수들의-합---1789) |
| 01 | <a href="https://www.acmicpc.net/problem/2417" target="_blank">2417</a> | <a href="https://www.acmicpc.net/problem/2417" target="_blank">정수 제곱근</a> | ![](/assets/images/s4.svg){: width="4%" height="4%"} | [바로가기](#정수-제곱근---2417) |
| 02 | <a href="https://www.acmicpc.net/problem/10815" target="_blank">10815</a> | <a href="https://www.acmicpc.net/problem/10815" target="_blank">숫자 카드</a> | ![](/assets/images/s4.svg){: width="4%" height="4%"} | [바로가기](#숫자-카드---10815) |
| 03 | <a href="https://www.acmicpc.net/problem/2805" target="_blank">2805</a> | <a href="https://www.acmicpc.net/problem/2805" target="_blank">나무 자르기</a> | ![](/assets/images/s3.svg){: width="4%" height="4%"} | [바로가기](#나무-자르기---2805) |
| 04 | <a href="https://www.acmicpc.net/problem/1654" target="_blank">1654</a> | <a href="https://www.acmicpc.net/problem/1654" target="_blank">랜선 자르기</a> |![](/assets/images/s3.svg){: width="4%" height="4%"} | [바로가기](#랜선-자르기---1654) |
| 05 | <a href="https://www.acmicpc.net/problem/2512" target="_blank">2512</a> | <a href="https://www.acmicpc.net/problem/2512" target="_blank">예산</a> | ![](/assets/images/s3.svg){: width="4%" height="4%"} | [바로가기](#예산---2512) |
| 06 | <a href="https://www.acmicpc.net/problem/19637" target="_blank">19637</a> | <a href="https://www.acmicpc.net/problem/19637" target="_blank">IF문 좀 대신 써줘</a> | ![](/assets/images/s3.svg){: width="4%" height="4%"} | [바로가기](#IF문-좀-대신-써줘---19637) |
| 07 | <a href="https://www.acmicpc.net/problem/11663" target="_blank">11663</a> | <a href="https://www.acmicpc.net/problem/11663" target="_blank">선분 위의 점</a> | ![](/assets/images/s3.svg){: width="4%" height="4%"} | [바로가기](#선분-위의-점---11663) |
| 08 | <a href="https://www.acmicpc.net/problem/22871" target="_blank">22871</a> | <a href="https://www.acmicpc.net/problem/22871" target="_blank">징검다리 건너기 (large)</a> | ![](/assets/images/s1.svg){: width="4%" height="4%"} | [바로가기](#징검다리-건너기-large---22871) |

</div>
</details>

---

# 문제
## 1. 문자열
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

let dict: [Character:Int] = ["A":3, "B":2, "C":1, "D":2, "E":3, "F":3, \
 "G":3, "H":3, "I":1, "J":1, "K":3, "L":1, "M":3, "N":3, "O":1, "P":2, \
 "Q":2, "R":2, "S":1, "T":2, "U":1, "V":1, "W":2, "X":2, "Y":2, "Z":1]

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

## 2. 이분 탐색

## 수들의 합 - 1789

~~~swift
import Foundation

let N = Int(readLine()!)!
var answer = 0
var i = 1
var sum = 0
while(true) {
    sum += i
    answer += 1
    i += 1
    if sum >= N {
        if sum == N {
            break
        }
        answer -= 1
        break
    }
}
print(answer)
~~~

## 정수 제곱근 - 2417
~~~swift
import Foundation

let n = UInt64(readLine()!)!
var start:UInt64 = 0
var end = UInt64(sqrt(Double(UInt64.max))) + 1
if n == 0 {
    print(0)
} else {
    while (start <= end) {
        let mid = (start + end) / 2
        
        if n <= mid * mid {
            end = mid - 1
        } else {
            start = mid + 1
        }
    }
    print(end + 1)
}
~~~

## 숫자 카드 - 10815
~~~swift
import Foundation

let n = Int(readLine()!)!
var myCard = readLine()!.split(separator: " ").map{ Int($0)! }
let m = Int(readLine()!)!
var checkCard = readLine()!.split(separator: " ").map{ Int($0)! }

myCard.sort()
for card in checkCard {
    var start = myCard.startIndex
    var end = myCard.endIndex - 1
    // end = n - 1
    // sequence.endIndex = sequence의 마지막 인덱스 + 1
    var flag = false
    while (start <= end) {
        let mid = (start + end) / 2
        if myCard[mid] >= card {
            if myCard[mid] == card {
                flag = true
            }
            end = mid - 1
        } else {
            start = mid + 1
        }
    }
    if flag {
        print(1, terminator: " ")
    } else {
        print(0, terminator: " ")
    }
}
~~~