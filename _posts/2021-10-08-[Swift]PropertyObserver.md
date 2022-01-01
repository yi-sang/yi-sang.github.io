---
title: 'Property Observer'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Property Observer

```swift
import UIKit

var myAge = 0 {
  willSet {
    print("값이 설정될 예정이다. / myAge: \(myAge)")
  }
  didSet {
    print("값이 설정되었다. / myAge: \(myAge)")
  }
}
print("myAge: \(mtAge)")
myAge = 20
// 값이 설정될 예정이다. / myAge: 0
// 값이 설정되었다. / myAge: 20
```

💡이름은 너무 어려워보이는데 간단하다.

Custom Button만들 때 사용해보긴 했는데 어떻게 보면 진짜 유용하게 사용할 수 있을 것같다.



# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

