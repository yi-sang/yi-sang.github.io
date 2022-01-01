---
title: 'if 조건문'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# if 조건문

```swift
import UIKit

var isDarkMode : Bool = false

if !isDarkMode {
    print("다크모드 아닙니다.")
} else {
    print("다크모드 입니다.")
}

if isDarkMode {
    print("다크모드 입니다.")
} else {
    print("다크모드 아닙니다.")
}

// 삼항 연산자
var title : String = isDarkMode == true ? "다크모드 입니다" : "다크모드가 아닙니다."

var title2 : String = isDarkMode ? "다크모드 입니다" : "다크모드가 아닙니다."

var title3 : String = !isDarkMode ? "다크모드가 아닙니다." : "다크모드 입니다"

```

💡 삼항연산자의 형태에 익숙해지면 코드가 훨씬 간결해지겠다!

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

