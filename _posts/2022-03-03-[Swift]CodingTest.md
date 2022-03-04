---
title: '스위프트로 코딩테스트 보기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# swift(codingtest)

## 서론
파이썬으로 코딩테스트를 준비해오다가 코딩테스트만을 위한 언어를 배우는 것이 흥미가 슬슬 떨어지기도 했고

실제로 알고리즘을 사용할 언어는 스위프트라는 생각이 들어서 스위프트를 한번 해보고 싶었다.

정보도 적고 swift를 지원하지 않는 시험도 있겠지만 정보야 찾아내면 되고, swift를 지원하는 시험을 보면 되지 않을까? 라는 안일한 생각을 가지고 도전해본다!

사실 동적 언어인 파이썬에 비해서 정적 언어인 스위프트는 타입의 변경, 옵셔널 처리, 배열의 슬라이싱, 큐와 같은 기본 라이브러리의 부재와 같은 불편한 점이 상당하겠지만 면접에 있어서 만큼은 유리할 수 있을 것 같고 내가 좋아하는 언어이니 끝까지 파보고 싶은 생각이 있다. 정 안되면 그때되서 돌아오지 뭐..

정리는 이 글에 다 녹여낼 생각
```swift
import Foundation
// 1. 입력
// func readLine(strippingNewline: Bool = true) -> String?
// 1-1) 강제 변환
var forceInput = readLine()!
print("input : \(forceInput)")

// 1-2) 옵셔널 바인딩
var optionalInput = readLine()
if let optionalInput = optionalInput {
    print("input : \(optionalInput)")
}

// 1-3) Int로 받기
var inputInt = Int(readLine()!)!

// 1-4) Double로 받기
var inputDouble = Double(readLine()!)!

// 1-5) array로 받기
// 1-5-1) components(separatedBy)
// func components(separatedBy separator: String) -> [String]
// Foundation 내부 함수
// 구분자를 여러 개로 할 수 있다.
import Foundation
var inputStringArray = forceInput.components(separateBy: " ")
var inputStringArray = forceInput.components(separateBy: [" ", ","])

// 1-5-2) split()
// func split(separator: Character, maxSplits: Int = Int.max, omittingEmptySubsequences: Bool = true) -> [Substring]
// separator: 쪼개려는 문자 단위
// maxSplits: 지정한 문자 단위로 얼마나 쪼갤지
// omittingEmptySubsequences: Bool값으로 결과값에서 빈 시퀀스의 포함 유무를 설정
// Swift 표준 라이브러리이기 때문에 Foundation필요 없다.
let input = forceInput.split(separator: " ")

// 1-6) map()
// map을 통해 클로저로써 String -> Any로 타입을 변경해준다
// func map<T>(_ transform: (Element) throws -> T) rethrows -> [T]
// 1-6-1) components
let inputDoubleArray2 = readLine()!.components(separatedBy: " ").map {Int($0)!}
let inputDoubleArray2 = readLine()!.components(separatedBy: [" "]).map {Double($0)!}

// 1-6-2) split
let inputIntArray1 = readLine()!.split(separator: " ").map {Int($0)!}
let inputIntArray1 = readLine()!.split(separator: " ").map {Double($0)!}

// 1-6-3) Other Way
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let lowercaseNames = cast.map { $0.lowercased() }
// 'lowercaseNames' == ["vivien", "marlon", "kim", "karl"]
let letterCounts = cast.map { $0.count }
// 'letterCounts' == [6, 6, 3, 4]

// 1-7) joined()
// func joined(separator: String = "") -> String
// 1-7-1) components
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

// 1-7-2) splits
print(helloWorld.split(separator: ","))
// Prints ["Hello", " World", " My", " Name", " Is", " Hyle"]
print(helloWorld.split(separator: ",").joined())
// Prints "Hello World My Name Is Hyle"
print(helloWorld.split(separator: ",").joined().split(separator: " "))
// Prints ["Hello", "World", "My", "Name", "Is", "Hyle"]

// 2. 출력
// func print(_ items: Any..., separator: String = " ", terminator: String = "\n")
// items - 여러 파라미터를 넣을 수 있음, separator - 구분자, terminator - end
let oneToFive = 1...5
print(oneToFive)
// Prints "1...5"

print(1.0, 2.0, 3.0, 4.0, 5.0, separator: " ... ")
// Prints "1.0 ... 2.0 ... 3.0 ... 4.0 ... 5.0"

for n in 1...5 {
    print(n, terminator: "")
}
// Prints "12345"

// 3. 문자열
// 3-1) 문자열 생성
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

// 3-2) 빈 문자열 확인
if emptyString.isEmpty {
    print("This is empty")
}

// 3-3) 문자열 수정
var helloWorld = "Hello, "
helloWorld += "World"
print(HelloWorld)

// 3-4) 문자열 개수
let str = "How many characters is this String"
print(string.count)

// 3-5) 문자열 인덱싱
print(helloWorld[helloWorld.startIndex])
// H
print(helloWorld[helloWorld.index(before: helloWorld.endIndex)])
// d
print(helloWorld[helloWorld.index(helloWorld.startIndex, offsetBy: 0)])
// H
print(helloWorld[helloWorld.index(helloWorld.endIndex, offsetBy: -1)])
// d
//문자열의 맨 마지막 문자 endIndex는 helloWorld의 마지막 글자인
//d의 위치인 9가 아닌 문자열의 전체 길이인 10을 반환하므로
// index(before: str.endIndex)나
// index(str.endIndex, offsetBy: -1)로 처리

// 3-6) 문자열 슬라이싱
helloWord = "Hello, World"
let index = helloWorld.firstIndex(of: ",") ?? helloWorld.endIndex
let prefixHelloWorld = String(helloWorld[..<index])
print(prefixHelloWorld)
// Prints "Hello"

// subString 인스턴스로 반환되기 때문에 String 인스턴스로 바꿔서 사용하자.
print(helloWorld[helloWorld.startIndex..<helloWorld.index(helloWorld.endIndex, offsetBy: -7)])
// Prints "Hello"

let strRange = helloWorld.index(helloWorld.startIndex, offsetBy: 5) ... helloWorld.index(before: helloWorld.endIndex)
print(helloWorld[strRange])
// Prints ", World"

let sameRange = helloWorld.index(helloWorld.startIndex, offsetBy: 5) ..< helloWorld.endIndex
print(helloWorld[sameRange])
// Prints ", World"

// 3-7) 문자열 삭제
helloWorld.removeSubrange(strRange)
print(helloWorld)
// Prints "Hello"

var measurements = [1.2, 1.5, 2.9, 1.2, 1.5]
measurements.removeSubrange(1 ..< 4)
print(measurements)
// Prints [1.2, 1.5]

// 3-8) 접두사, 접미사 비교
//hasPrefix("H"): 문자열이 H로 시작하는지 확인 -> Bool 타입으로 반환
//hasSuffix("d"): 문자열이 d로 끝나는지 확인 -> Bool 타입으로 반환
helloWorld = "Hello, World"
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

> 2022.03.03 코테를 준비하면서 꾸준히 정리해나갈 예정
# More
