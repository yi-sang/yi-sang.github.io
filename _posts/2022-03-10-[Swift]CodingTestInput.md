---
title: '입력: 스위프트로 코딩테스트 보기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# 입력
`func readLine(strippingNewline: Bool = true) -> String?`

## 1) 강제 변환
``` swift
var forceInput = readLine()!

print("input : \(forceInput)")
```

## 2) 옵셔널 바인딩
``` swift
var optionalInput = readLine()

if let optionalInput = optionalInput {
    print("input : \(optionalInput)")
}
```

## 3) Int로 받기
``` swift
var inputInt = Int(readLine()!)!
```

## 4) Double로 받기
``` swift
var inputDouble = Double(readLine()!)!
```

## 5) array로 받기
## 5-1) components(separatedBy)
`func components(separatedBy separator: String) -> [String]`

Foundation 내부 함수

구분자를 여러 개로 할 수 있다.

``` swift
import Foundation

var inputStringArray = forceInput.components(separateBy: " ")
var inputStringArray = forceInput.components(separateBy: [" ", ","])
```
## 5-2) split()
`func split(separator: Character, maxSplits: Int = Int.max, omittingEmptySubsequences: Bool = true) -> [Substring]`

separator: 쪼개려는 문자 단위

maxSplits: 지정한 문자 단위로 얼마나 쪼갤지

omittingEmptySubsequences: Bool값으로 결과값에서 빈 시퀀스의 포함 유무를 설정

Swift 표준 라이브러리 (Foundation필요 X)
``` swift
let input = forceInput.split(separator: " ")
```
## 6) map()
문자열 -> 배열

클로저로써 String -> [Any] 타입 변환

`func map<T>(_ transform: (Element) throws -> T) rethrows -> [T]`

## 6-1) components
```swift
let inputDoubleArray2 = readLine()!.components(separatedBy: " ").map { Int($0)! }
let inputDoubleArray2 = readLine()!.components(separatedBy: [" "]).map { Double($0)! }
```

## 6-2) split
```swift
let inputIntArray1 = readLine()!.split(separator: " ").map { Int($0)! }
let inputIntArray1 = readLine()!.split(separator: " ").map { Double($0)! }
```

## 6-3) Other Way
```swift
let cast = ["Vivien", "Marlon", "Kim", "Karl"]

let lowercaseNames = cast.map { $0.lowercased() }
// 'lowercaseNames' == ["vivien", "marlon", "kim", "karl"]
let letterCounts = cast.map { $0.count }
// 'letterCounts' == [6, 6, 3, 4]
```

## 7) joined()
String -> [Any]
`func joined(separator: String = "") -> String`
## 7-1) components
```swift
helloWorld = "Hello, World, My, Name, Is, Hyle"

print(helloWorld.components(separatedBy: ","))
// Prints ["Hello", " World", " My", " Name", " Is", " Hyle"]

print(helloWorld.components(separatedBy: ",").joined())
// Prints "Hello World My Name Is Hyle"

print(helloWorld.components(separatedBy: ",").joined().components(separatatedBy: " "))
// Prints ["Hello", "World", "My", "Name", "Is", "Hyle"]

print(helloWorld.components(separatedBy: [",", " "]))
// Prints ["Hello", "", "World", "", "My", "", "Name", "", "Is", "", "Hyle"]

print(helloWorld.components(separatedBy: [",", " "]).joined())
// Prints "HelloWorldMyNameIsHyle"
```

## 7-2) splits
```swift
print(helloWorld.split(separator: ","))
// Prints ["Hello", " World", " My", " Name", " Is", " Hyle"]

print(helloWorld.split(separator: ",").joined())
// Prints "Hello World My Name Is Hyle"

print(helloWorld.split(separator: ",").joined().split(separator: " "))
// Prints ["Hello", "World", "My", "Name", "Is", "Hyle"]
```