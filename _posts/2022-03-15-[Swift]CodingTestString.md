---
title: '문자열: 스위프트로 코딩테스트 보기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# 문자열
String은 Character로 구성되어 있다.
```swift

let str = "Hyle"
print(type(of: str.first!))
// Prints "Character"
```

## 1) 문자열 생성
```swift
var emptyString = ""
var initEmptyString = String()

let price = 2
let number = 3
let cookiePrice = "\(number) cookies: $\(price * number)."
print(cookiePrice)
// Prints "3 cookies: $6."

let banner = """
          __,
         (           o  /) _/_
          `.  , , , ,  //  /
        (___)(_(_/_(_ //_ (__
                     /)
                    (/
        """
// Prints "
//  __,
// (           o  /) _/_
//  `.  , , , ,  //  /
//(___)(_(_/_(_ //_ (__
//             /)
//            (/"
```
## 2) 빈 문자열 확인
```swift
let emptyString = ""

if emptyString.isEmpty {
    print("This is empty")
}
// Prints "This is empty"
```

## 3) 문자열 수정
```swift
var helloWorld = "Hello, "
helloWorld += "World"
print(HelloWorld)
// Print "Hello, World"
```

## 4) 문자열 개수
```swift
let str = "How many characters is this String"
print(string.count)
// Prints "34"
```

## 5) 문자열 인덱싱
다른 언어와 같은 경우 str[Int] 형태로 접근가능하지만,

Swift의 경우 str[String.Index]의 형태로 접근해야한다.
문자열의 맨 마지막 문자 endIndex는 helloWorld의 마지막 글자인

d의 위치인 9가 아닌 문자열의 전체 길이인 10을 반환하므로

index(before: str.endIndex)나

index(str.endIndex, offsetBy: -1)로 처리
```swift
var helloWorld = "Hello, World"

print(helloWorld[helloWorld.startIndex])
// H

print(helloWorld[helloWorld.index(before: helloWorld.endIndex)])
// d

print(helloWorld[helloWorld.index(helloWorld.endIndex, offsetBy: -1)])
// d

print(helloWorld[helloWorld.index(helloWorld.startIndex, offsetBy: 0)])
// H

print(helloWorld[helloWorld.index(after: helloWorld.startIndex)])
// e
```

## 6) 문자열 슬라이싱
Substring 인스턴스로 반환되기 때문에 String 인스턴스로 바꿔서 사용하자.
```swift
var helloWorld = "Hello, World"
let index = helloWorld.firstIndex(of: ",") ?? helloWorld.endIndex

print(type(of: prefixHelloWorld))
// Prints "Substring"

let prefixHelloWorld = String(helloWorld[..<index])

print(type(of: prefixHelloWorld))
// Prints "String"

print(prefixHelloWorld)
// Prints "Hello"

print(helloWorld[helloWorld.startIndex..<helloWorld.index(helloWorld.endIndex, offsetBy: -7)])
// Prints "Hello"

let strRange = helloWorld.index(helloWorld.startIndex, offsetBy: 5) ... helloWorld.index(before: helloWorld.endIndex)
print(helloWorld[strRange])
// Prints ", World"

let sameRange = helloWorld.index(helloWorld.startIndex, offsetBy: 5) ..< helloWorld.endIndex
print(helloWorld[sameRange])
// Prints ", World"
```
## 3-7) 문자열 삭제
```swift
var helloWorld = "Hello, World"

let strRange = helloWorld.index(helloWorld.startIndex, offsetBy: 5) ... helloWorld.index(before: helloWorld.endIndex)
helloWorld.removeSubrange(strRange)
print(helloWorld)
// Prints "Hello"

var measurements = [1.2, 1.5, 2.9, 1.2, 1.5]
measurements.removeSubrange(1 ..< 4)
print(measurements)
// Prints [1.2, 1.5]
```

## 3-8) 접두사, 접미사 비교
hasPrefix("H"): 문자열이 H로 시작하는지 확인 -> Bool 타입으로 반환

hasSuffix("d"): 문자열이 d로 끝나는지 확인 -> Bool 타입으로 반환
```swift
var helloWorld = "Hello, World"
print(helloWorld.hasPrefix("H"))
// true

print(helloWorld.hasPrefix("a"))
// false

if helloWorld.hasPrefix("H") {
    print("H 로 시작하는 문자열 입니다.")
}
// Prints "H 로 시작하는 문자열 입니다."
if helloWorld.hasSuffix("d") {
    print("d 로 끝나는 문자열 입니다.")
}
// Prints "d 로 끝나는 문자열 입니다."

print(helloWorld.uppercased())
// Prints "HELLO, WORLD"

print(helloWorld.lowercased())
// Prints "hello, world" 
```
# More
