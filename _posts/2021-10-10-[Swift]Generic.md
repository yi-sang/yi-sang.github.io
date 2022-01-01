---
title: '제네릭'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 제네릭

```swift
import UIKit

struct MyArray<T>{
    
    // 제네릭을 담은 빈 배열
    var elements : [T] = [T]()
    
    // 생성자
    init(_ elements: [T]){
        self.elements = elements
    }
}

struct Friend {
    var name: String
}

struct PpakCoder {
    var name: String
}

var mySomeArray = MyArray([1,2,3])
print("mySomeArray : \(mySomeArray)")
// mySomeArray: MyArray<Int> = {
//  elements = 3 values {
//    [0] = 1
//    [1] = 2
//    [2] = 3
//  }
//}
var myStringArray = MyArray(["가","나","다"])
print("myStringArray : \(myStringArray)")
// myStringArray: MyArray<String> = {
//   elements = 3 values {
//     [0] = "가"
//     [1] = "나"
//     [2] = "다"
//   }
// }
let friend_01 = Friend(name: "철수")
let friend_02 = Friend(name: "영희")
let friend_03 = Friend(name: "수잔")

var myFriendsArray = MyArray([friend_01,friend_02,friend_03])
print("myFriendsArray : \(myFriendsArray)")
// myFriendsArray: MyArray<Friend> = {
//   elements = 3 values {
//     [0] = {
//       name = "철수"
//     }
//     [1] = {
//       name = "영희"
//     }
//     [2] = {
//       name = "수잔"
//     }
//   }
// }
```

💡 어떤 형태의 type이 들어가도 되는 type이다.



# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])
