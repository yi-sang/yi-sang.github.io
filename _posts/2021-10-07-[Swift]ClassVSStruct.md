---
title: 'Class vs Struct'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Class vs Struct

```swift
import UIKit

// 유튜버 (데이터) 모델 - struct / 구조체
struct YoutuberStruct {
    var name : String
    var subscribersCount : Int
}

var devJeong = YoutuberStruct(name: "정대리", subscribersCount: 99999)

var devJeongClone = devJeong

print("======== struct =========")

print("값 넣기 전 devJeongClone.name : \(devJeongClone.name)")

devJeongClone.name = "호롤롤로"

// 값 복사이기 때문에 둘의 값이 다르다
print("값 넣은 후 devJeongClone.name : \(devJeongClone.name)")
print("값 넣은 후 devJeong.name : \(devJeong.name)")

print("======== class =========")

// 클래스
class YoutuberClass {
    var name : String
    var subscribersCount : Int
    // 생성자 - 즉 메모리에 올린다
    // init 으로 매개변수를 가진 생성자 메소드를 만들어야
    // 매개변수를 넣어서 그값을 가진 객체(object)를 만들수 있다.
    init(name: String, subscribersCount: Int){
        self.name = name
        self.subscribersCount = subscribersCount
    }
}

var jeongDaeRi = YoutuberClass(name: "정대리", subscribersCount: 99999)

var jeongDaeRiClone = jeongDaeRi

print("값 넣기 전 jeongDaeRiClone.name : \(jeongDaeRiClone.name)")

jeongDaeRiClone.name = "호롤롤롤로"

print("값 넣은 후 jeongDaeRiClone.name : \(jeongDaeRiClone.name)")
print("값 넣은 후 jeongDaeRi.name : \(jeongDaeRi.name)")
```

💡 지금의 나는 딱히 참조할만 한 상황이 주어지지 않는 것 같고 init을 따로 해주기 싫어서 struct를 많이 사용하는 데 미래의 나는 어떨까

| Class                     |  Vs   | Struct                      |
| ------------------------- | :---: | --------------------------- |
| 단일 상속                 | <---> | 상속 불가                   |
| 참조 타입                 | <---> | 값 타입                     |
| Apple 프레임워크의 대부분 | <---> | Swift의 프레임워크의 대부분 |




# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

