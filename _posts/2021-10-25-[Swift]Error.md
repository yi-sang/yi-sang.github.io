---
title: 'Error'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Error

```swift
import UIKit

enum MismatchError: Error {
    case nameMismatch
    case numberMismatch
}

// 에러를 던지는 메소드
func guessMyName(name input: String) throws {
    print("guessMyName() called")

    if input != "hyle" {
        print("틀렸다.")
        throw MismatchError.nameMismatch
        // return과 비슷한 역할
    }

    print("맞췄다")
}
try? guessMyName(name: "이대리")
// error가 있든 없든 처리X
try! guessMyName(name: "이대리")
// error가 없을 거야!
do {
    try guessMyName(name: "이대리")
} catch {
    print("잡은 에러 \(error)")
}

// 에러를 던지는 메소드(반환형이 있는)
func guessMyNumber(number input: Int) throws -> Bool {
    print("guessMyNumber() called")

    if input != 10 {
        print("틀렸다.")
        throw MismatchError.numberMismatch
    }

    print("맞췄다")
    return true
}

do {
    let receivedValue = try guessMyNumber(number: 10)
} catch {
    print("잡은 에러 \(error)")
}
```

💡 alt + cmd + / 주석 처리

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])





