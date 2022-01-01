---
title: 'Unwrap 옵셔널 변수'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Unwrap 옵셔널 변수

```swift
import UIKit

// 값이 있는지 없는지 모른다.
var someVariable : Int? = nil


// If Statements
if someVariable == nil {
    someVariable = 90
}

print("someVariable: ", someVariable)

// 언랩핑이란? 랩 즉 감싸져있는 것을 벗기는 것
// Optional Binding
if let otherVariable = someVariable {
    print("언래핑 되었다. 즉 값이 있다. otherVariable : \(otherVariable)")
} else {
    print("값이 없다.")
}

someVariable = nil

// 닐 병합 연산
let myValue = someVariable ?? 10
print("myValue: \(myValue)")

var firstValue : Int? = 30
var secondValue : Int? = 50

print("firstValue: \(firstValue)")
print("secondValue: \(secondValue)")

unwrap(firstValue)
// unWrappedParam: 30
unwrap(secondValue)
// unWrappedParam: 50

func unwrap(_ parameter: Int?) {
    print("unwrap() called")
    
    guard let unWrappedParam = parameter else { return }
    print("unWrappedParam: \(unWrappedParam)")
}
```

💡뭔지는 다 알겠는데 정확히 지칭하는 명칭에 대해서는 확실하지 않다.

일단은 지나가자. 우선은 매일 같이 하는 것이 중요할 것 같다.

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

