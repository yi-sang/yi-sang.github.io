---
title: '파이널 클래스'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 파이널 클래스

```swift
import UIKit


final class Friend {
    
    var name : String
    
    init(name: String){
        self.name = name
    }
}
// 오류 발생
class BestFriend : Friend {
    
    override init(name: String) {
        super.init(name: "베프 " + name)
    }
}

let myFriend = Friend(name: "쩡대리")
let myBestFriend = BestFriend(name: "철수")
```

💡final 이 있네? 상속이 안 된다!

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])





