---
title: '스트럭트 메소드'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 스트럭트 메소드

```swift
import UIKit

// struct 에서도 메소드를 가질수 있습니다.
struct Friend {
    
    var age : Int
    
    var name : String
    
    func sayHello() -> String {
        print("sayHello()")
        return "저는 \(age)살, \(name) 입니다."
    }
}

var myFriend = Friend(age: 28, name: "Hyle")

myFriend.sayHello()
```
💡
# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])


