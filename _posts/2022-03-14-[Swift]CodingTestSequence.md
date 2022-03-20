---
title: '시퀀스: 스위프트로 코딩테스트 보기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# 시퀀스
시퀀스란? 요소에 대한 순차적이고 반복적인 액세스를 제공하는 유형.

Array, String와 같은 반복자가 가지고 있는 프로토콜이다.

Swift는 일반적인 C와 같이 인덱스 하나하나에 접근하기가 불편한 점이 많다.

하지만 Swift는 함수형 프로그래밍이라는 이름에 걸맞게 여러 함수가 많다.

잘만 활용한다면 상당히 편할 것 같다!

Sequence프로토콜을 채택한 자료형은 어떠한 함수를 쓸 수 있을지 알아보자.

설명보다는 예시를 보고 이해하자.

생략된 것도 있다!
## 요소 찾기
## `contains()`
return (포함해 ? true : false)

`func contains(Self.Element) -> Bool`
```Swift
let cast = ["Vivien", "Marlon", "Kim", "Karl"]

print(cast.contains("Marlon"))
// Prints "true"
print(cast.contains("James"))
// Prints "false"
```

## `contains(where:)`
return ({ 조건 } 포함해 ? true : false)

`func contains(where: (Self.Element) -> Bool) -> Bool`
```Swift
let expenses = [21.37, 55.21, 9.32, 10.18, 388.77, 11.41]
let hasBigPurchase = expenses.contains { $0 > 100 }
// 'hasBigPurchase' == true
```

## `allSatisfy(_:)`
return (모든 요소들이 만족해 ? true : false)

`func allSatisfy((Self.Element) -> Bool) -> Bool`
```Swift
let names = ["Sofia", "Camilla", "Martina", "Mateo", "Nicolás"]
let allHaveAtLeastFive = names.allSatisfy({ $0.count >= 5 })
// allHaveAtLeastFive == true
```

## `first(where:)`
return (처음 { 조건 } 만족하는 ? 요소 : nil)

`func first(where: (Self.Element) -> Bool) -> Self.Element?`
```Swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
if let firstNegative = numbers.first(where: { $0 < 0 }) {
    print("The first negative number is \(firstNegative).")
}
// Prints "The first negative number is -2."
```

## `min()`
return (제일 작은 ? 요소 : nil()

`func min() -> Self.Element?`
```Swift
let heights = [67.5, 65.7, 64.3, 61.1, 58.5, 60.3, 64.9]
let lowestHeight = heights.min()
print(lowestHeight)
// Prints "Optional(58.5)"
```

## `min(by:)`
return (제일 작은 ? 요소 : nil())

`func min(by: (Self.Element, Self.Element) -> Bool) -> Self.Element?`
```Swift
let hues = ["Heliotrope": 296, "Coral": 16, "Aquamarine": 156]
let leastHue = hues.min { a, b in a.value < b.value }
print(leastHue)
// Prints "Optional((key: "Coral", value: 16))"
```

## `max()`
return (제일 큰 ? 요소 : nil())

`func max() -> Self.Element?`
```Swift
let heights = [67.5, 65.7, 64.3, 61.1, 58.5, 60.3, 64.9]
let greatestHeight = heights.max()
print(greatestHeight)
// Prints "Optional(67.5)"
```

## `max(by:)`
return (제일 큰 ? 요소 : nil())

`func max(by: (Self.Element, Self.Element) -> Bool) -> Self.Element?`
```Swift
let hues = ["Heliotrope": 296, "Coral": 16, "Aquamarine": 156]
let greatestHue = hues.max { a, b in a.value < b.value }
print(greatestHue)
// Prints "Optional((key: "Heliotrope", value: 296))"
```

## 요소 선택하기
## `prefix(Int)`
return (0번째 요소부터 Int번째까지의 [Self.Element])

`func prefix(Int) -> PrefixSequence<Self>`
```Swift
let numbers = [1, 2, 3, 2, 4, 5]
print(numbers.prefix(2))
// Prints "[1, 2]"
print(numbers.prefix(4))
// Prints "[1, 2, 3, 2]"
print(type(of: numbers.prefix(4)))
// Prints "ArraySlice<Int>"
let str = "Hyle"
print(type(of: str.prefix(2)))
// Prints "Substring"
```

## `prefix(while:)`
return (0번째 요소부터 { 조건 }을 만족하는 [Self.Element])

`func prefix(while: (Self.Element) -> Bool) -> [Self.Element]`
```Swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let positivePrefix = numbers.prefix(while: { $0 > 0 })
// positivePrefix == [3, 7, 4]
```

## `suffix(Int)`
return (뒤의 요소부터 Int번째까지의 [Self.Element])

`func suffix(Int) -> [Self.Element]`
```Swift
let numbers = [1, 2, 3, 4, 5]
print(numbers.suffix(2))
// Prints "[4, 5]"
print(numbers.suffix(10))
// Prints "[1, 2, 3, 4, 5]"
```

## 요소 포함하기
## `dropFirst(Int)`
return (0번째 요소부터 Int번째까지의 요소를 탈락시키는 [Self.Element])

`func dropFirst(Int) -> DropFirstSequence<Self>`
```Swift
let numbers = [1, 2, 3, 4, 5]
print(numbers.dropFirst(2))
// Prints "[3, 4, 5]"
print(numbers.dropFirst(10))
// Prints "[]"
```

## `dropLast(Int)`
`func dropLast(Int) -> [Self.Element]`

return (뒤의 요소부터 Int번째까지 요소를 탈락시키는 [Self.Element])
```Swift
let numbers = [1, 2, 3, 4, 5]
print(numbers.dropLast(2))
// Prints "[1, 2, 3]"
print(numbers.dropLast(10))
// Prints "[]"
```

## `drop(while:)`
`func drop(while: (Self.Element) -> Bool) -> DropWhileSequence<Self>`

return ({ 조건 } 에 부합하지 않을 때까지 0번째 요소부터 차례로 탈락시키는 [Self.Element])
```Swift
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let startingWithNegative = numbers.drop(while: { $0 > 0 })
// startingWithNegative == [-2, 9, -6, 10, 1]
```

## `filter(_:)`
`func filter((Self.Element) -> Bool) -> [Self.Element]`

return ({ 조건 } 에 부합하는 요소들만 추려진 [Self.Element])
```Swift
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let shortNames = cast.filter { $0.count < 5 }
print(shortNames)
// Prints "["Kim", "Karl"]"
```

## 시퀀스 변형하기
## `map(_:)`
`func map<T>((Self.Element) -> T) -> [T]`

return ({ 조건 } 에 부합하도록 요소를 변형시킨 [Self.Element])
```Swift
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let lowercaseNames = cast.map { $0.lowercased() }
// 'lowercaseNames' == ["vivien", "marlon", "kim", "karl"]
let letterCounts = cast.map { $0.count }
// 'letterCounts' == [6, 6, 3, 4]
```

## `compactMap(_:)`
`func compactMap<ElementOfResult>((Self.Element) -> ElementOfResult?) -> [ElementOfResult]`

return (optional을 unwrapping 하고 nil이 있다면 제외하는 [Self.Element])
```Swift
let possibleNumbers = ["1", "2", "three", "///4///", "5"]
let mapped: [Int?] = possibleNumbers.map { str in Int(str) }
print(mapped)
// [Optional(1), Optional(2), nil, nil, Optional(5)]

let compactMapped: [Int] = possibleNumbers.compactMap { str in Int(str) }
print(compactMapped)
// [1, 2, 5]
```

## `flatMap(_:)`
`func flatMap<SegmentOfResult>((Self.Element) -> SegmentOfResult) -> [SegmentOfResult.Element]`

return (sequence안의 sequence 각각을 extend하는 [Self.Element])
```Swift
let numbers = [1, 2, 3, 4]

let mapped = numbers.map { Array(repeating: $0, count: $0) }
// [[1], [2, 2], [3, 3, 3], [4, 4, 4, 4]]

let flatMapped = numbers.flatMap { Array(repeating: $0, count: $0) }
// [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
```

## `reduce(_:_:)`
return (주어진 클로저를 이용하여 시퀀스의 요소를 결합한 value)

`func reduce<Result>(Result, (Result, Self.Element) -> Result) -> Result`
```Swift
let numbers = [1, 2, 3, 4]
let numberSum = numbers.reduce(0, { x, y in
    x + y
})
// numberSum == 10
```

## `reduce(into:_:)`
return  (주어진 클로저를 이용하여 시퀀스의 요소를 결합한 sequence)

`func reduce<Result>(into: Result, (inout Result, Self.Element) -> ()) -> Result`
```Swift
let letters = "abracadabra"
let letterCount = letters.reduce(into: [:]) { counts, letter in
    counts[letter, default: 0] += 1
}
// letterCount == ["a": 5, "b": 2, "r": 2, "c": 1, "d": 1]
```

## `lazy`
`var lazy: LazySequence<Self>`

이 시퀀스와 동일한 요소를 포함하지만 맵과 필터와 같은 일부 작업이 lazy하게 구현되는 시퀀스.

## 요소 반복하기
## `forEach(_:)`
for-in루프와 같은 역할을 하지만 주어진 클로저를 이용하여 사용.

`func forEach((Self.Element) -> Void)`
```Swift
let numberWords = ["one", "two", "three"]
for word in numberWords {
    print(word)
}
// Prints "one"
// Prints "two"
// Prints "three"

numberWords.forEach { word in
    print(word)
}
// Same as above
```

## `enumerated()`
(index, value) 형태로 Sequence의 요소를 받을 수 있다.

`func enumerated() -> EnumeratedSequence<Self>`
```Swift
for (n, c) in "Swift".enumerated() {
    print("\(n): '\(c)'")
}
// Prints "0: 'S'"
// Prints "1: 'w'"
// Prints "2: 'i'"
// Prints "3: 'f'"
// Prints "4: 't'"
```

## `underestimatedCount()`
비파괴적으로 계산된, 시퀀스에서 요소의 수와 같거나 작은 value.
Required.

`var underestimatedCount: Int`

## 요소 정렬하기
## `sorted()`
return (정렬된 Array)

`func sorted() -> [Self.Element]`
```Swift
let students: Set = ["Kofi", "Abena", "Peter", "Kweku", "Akosua"]
let sortedStudents = students.sorted()
print(sortedStudents)
// Prints "["Abena", "Akosua", "Kofi", "Kweku", "Peter"]"
```

## `sorted(by:)`
return (조건자를 이용하여 정렬할 방향을 구한후 정렬된 Array)

`func sorted(by: (Self.Element, Self.Element) -> Bool) -> [Self.Element]`
```Swift
let descendingStudents = students.sorted(by: >)
print(descendingStudents)
// Prints "["Peter", "Kweku", "Kofi", "Akosua", "Abena"]"
```

## `reversed()`
return (reversed 요소들을 포함하는 Array)

`func reversed() -> [Self.Element]`
```Swift
let numArray = 0...9
let reversedNumArray = numArray.reversed()
print(Array(reversedNumArray))
// Prints "[4, 2, 1, 0]"
```

## 요소 재정렬하기
## `shuffled()`
return (shuffled 요소들을 포함하는 Array))

`func shuffled() - > [Self.Element]`
```Swift
let numbers = 0...9
let shuffledNumbers = numbers.shuffled()
// shuffledNumbers == [1, 7, 6, 2, 8, 9, 4, 3, 5, 0]
```

## `formatted()`
return (sequence의 요소들이 String일 때 default list format 스타일로 표현되어진 String)

`func formatted() -> String`
```Swift
["Kristin", "Paul", "Ana", "Bill"].formatted()
// Kristin, Paul, Ana, and Bill
```

## `formatted(_:)`
return (sequence의 요소들이 String일 때 제공하는 list format 스타일로 표현되어진 String)

`func formatted<S>(S) -> S.FormatOutput`
```Swift
[1, 3, 5, 7].formatted(.list(memberStyle: .descriptive, type: .and, width: .narrow))
// "one, three, five, & seven"

(5201719 ... 5201722).formatted(.list(memberStyle: IntegerFormatStyle(), type: .or, width: .standard))
// For locale: en_US: 5,201,719, 5,201,720, 5,201,721, or 5,201,722
// For locale: fr_CA: 5 201 719, 5 201 720, 5 201 721, ou 5 201 722

let percentStyle = ListFormatStyle<FloatingPointFormatStyle.Percent, StrideThrough<Double>>(memberStyle: .percent)
stride(from: 7.5, through: 9.0, by: 0.5).formatted(percentStyle)
// 7.5%, 8%, 8.5%, and 9%
stride(from: 89.0, through: 95.0, by: 2.0).formatted(percentStyle)
// 89%, 91%, 93%, and 95%
```

## `split(maxSplits:omittingEmptySubsequences:whereSeparator:)`
return (Sequence를 isSeparator 클로저에 의해 구분되어진 [Self.Element])
maxSplits: 몇 번 분리할 건지, 리턴되어질 요소의 개수 - 1, 0보다 크고 Int의 최대값보다 작다., default = Int의 최대값

omittingEmptySubsequences: if false, 공백 포함 / if ture, 공백 제외

isSeparator(내부에서 사용할 파라미터 이름) == whereSeparator(외부에서 사용할 파라미터 이름):
sequence를 분리할 구분자를 클로저를 통해서 전달한다.

`func split(maxSplits: Int, omittingEmptySubsequences: Bool, whereSeparator: (Self.Element) -> Bool) -> [ArraySlice<Self.Element>]`
```Swift
let line = "BLANCHE:   I don't want realism. I want magic!"
print(line.split(whereSeparator: { $0 == " " })
        .map{ String($0) })
//print(line.split(whereSeparator: { $0 == " " })
//      .map(String.init))
// Prints "["BLANCHE:", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"

print(
   line.split(maxSplits: 1, whereSeparator: { $0 == " " })
                  .map(String.init))
// Prints "["BLANCHE:", "  I don\'t want realism. I want magic!"]"

print(
    line.split(
        omittingEmptySubsequences: false,
        whereSeparator: { $0 == " " }
    ).map(String.init))
// Prints "["BLANCHE:", "", "", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

## `split(separator:maxSplits:omittingEmptySubsequences:)`
return (Sequence를 separator에 의해 구분되어진 [Self.Element])

요소가 Equatable 프로토콜을 수용할 때 가능.

separator: 구분자

`func split(separator: Self.Element, maxSplits: Int = Int.max, omittingEmptySubsequences: Bool = true) -> [ArraySlice<Self.Element>]`
```Swift
let line = "BLANCHE:   I don't want realism. I want magic!"
print(line.split(separator: " ")
          .map(String.init))
// Prints "["BLANCHE:", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"

print(line.split(separator: " ", maxSplits: 1)
          .map(String.init))
// Prints "["BLANCHE:", "  I don\'t want realism. I want magic!"]"


print(line.split(separator: " ", omittingEmptySubsequences: false)
          .map(String.init))
// Prints "["BLANCHE:", "", "", "I", "don\'t", "want", "realism.", "I", "want", "magic!"]"
```

## `joined()`
return (시퀀스들의 시퀀스의 연속된 요소들)

`func joined() -> FlattenSequence<Self>`
```Swift
let ranges = [0..<3, 8..<10, 15..<17]

// A for-in loop over 'ranges' accesses each range:
for range in ranges {
  print(range)
}
// Prints "0..<3"
// Prints "8..<10"
// Prints "15..<17"

// Use 'joined()' to access each element of each range:
for index in ranges.joined() {
    print(index, terminator: " ")
}
// Prints: "0 1 2 8 9 15 16"
```

## `joined(separator:)`
return (saparator로 구분지어진 시퀀스들의 시퀀스의 연속된 요소들)

`func joined(separator: String = "") -> String`
```Swift
let cast = ["Vivien", "Marlon", "Kim", "Karl"]
let list = cast.joined(separator: ", ")
print(list)
// Prints "Vivien, Marlon, Kim, Karl"
```

## `joined(separator:)`
return (saparator로 구분지어진 시퀀스들의 시퀀스의 연속된 요소들)

`func joined<Separator>(separator: Separator) -> JoinedSequence<Self>`
```Swift
let nestedNumbers = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
let joined = nestedNumbers.joined(separator: [-1, -2])
print(Array(joined))
// Prints "[1, 2, 3, -1, -2, 4, 5, 6, -1, -2, 7, 8, 9]"
```

## 시퀀스 비교하기
## `elementsEqual(_:)`
return (같은 시퀀스(같은 요소, 순서) ? true : false)

`func elementsEqual<OtherSequence>(OtherSequence) -> Bool`
```Swift
let a = 1...3
let b = 1...10

print(a.elementsEqual(b))
// Prints "false"
print(a.elementsEqual([1, 2, 3]))
// Prints "true"
```

## `starts(with:)`
return (시퀀스가 다른 시퀀스로 시작해 ? true : false)

`func starts<PossiblePrefix>(with: PossiblePrefix) -> Bool`
```Swift
let a = 1...3
let b = 1...10

print(b.starts(with: a))
// Prints "true"

```

## `lexicographicallyPrecedes(_:)`
return (sequence가 사전순으로 앞에 있어 ? true : false)

`func lexicographicallyPrecedes<OtherSequence>(OtherSequence) -> Bool`
```Swift
let a = [1, 2, 2, 2, 3]
let b = [1, 2, 3, 4]

print(a.lexicographicallyPrecedes(b))
// Prints "true"
print(b.lexicographicallyPrecedes(b))
// Prints "false"
```

# More
[Apple 공식 문서 - Sequence](https://developer.apple.com/documentation/swift/sequence)

결국 공식 문서에 답이 있었다.

이전에 나는 왜 공식문서를 안 봤는 지 자책하기 보다는

이제 필요성을 느꼈고 흥미가 생겼으니 이제부터라도 보면 된다는 생각을 가지자!

외워서 잘 활용할 수 있었으면 좋겠다! 

RxSwift나 MVVM과 같은 경우도 해야한다해서 볼 때는 이해가 안 됐는데 이제 내가 불편함을 가지고 찾아보다보니 이해가 잘 되고 재밌게 공부할 수 있는 것 같다.
