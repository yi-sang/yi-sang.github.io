---
title: '클로저'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 클로저

```swift
import UIKit

// String을 반환하는 클로저
let myName : String = {
    // myName 으로 들어간다
    return "정대리"
}()

print(myName)

// 클로저 정의
let myRealName : (String) -> String = { (name: String) -> String in
    return "개발하는 \(name)"
}
// 축약
let myRealName : (String) -> String = { (name: String) in
    return "개발하는 \(name)"
}
// 축약
let myRealName : (String) -> String = { name in
    return "개발하는 \(name)"
}

myRealName("쩡대리")

let myRealNameLogic : (String) -> Void = { (name: String) in
    print("개발하는 \(name)")
}

myRealNameLogic("정대리 호롤롤로")
```

💡 클로저를 사용하면 변수와 함수의 구분선이 없어지는 것 같다.



# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])



