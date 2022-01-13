---
title: '딕셔너리'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 상속

> 콜렉션중 하나
>
> 키 - 값
>
> 키로 자물쇠를 연다!
>
> 해쉬 테이블의 종류

```swift
import UIKit

// 키 값으로 한쌍인 딕셔너리 - 사물함과 비슷
// 키 : 값
var myFriends = ["bestFriend" : "쩡대리",
                 "highschool" : "영희"
                ]

// bestFriend 라는 열쇠로 내용물을 꺼냄
let myBestFriend = myFriends["bestFriend"]
let highSchoolFriend = myFriends["highschool"]

// 해당 키로 값을 꺼낼때 저장된 값이 없다면 default 로 기본 값을 가져오도록 설정 가능
let youtubeFriend = myFriends["youtube" , default: "친구없음"]

// 값 추가 및 변경 가능
myFriends["bestFriend"] = "개발하는 정대리"

let myBF = myFriends["bestFriend"] //개발하는 정대리

myFriends["newFriend"] = "철수"

let newFriend = myFriends["newFriend"] // 철수

// updateValue 메소드로 값 추가 및 변경 가능
myFriends.updateValue("수잔", forKey: "girlFriend")

let girlFriend = myFriends["girlFriend"]

myFriends.updateValue("짹슨", forKey: "bestFriend")
// 이해하기 쉽겠다!

let myBestFriend2 = myFriends["bestFriend"]

// 빈 딕셔너리를 만드는 방법 들
let emptyDictionary1 : [String : Int] = [:]
let emptyDictionary2 = [String : Int]()

let myEmptyDictionary : [String : Int] = Dictionary<String, Int>()
// Result<success, failure>와 같은 형태
myFriends.count

for item in myFriends {
    print("item : ",item)
}
```

💡

- Default 지정

​	`let youtubeFriend = myFriends["youtube" , default: "친구없음"]` 

- updateValue("anyValue", forKey: "anyKey")

​	`myFriends.updateValue("짹슨", forKey: "bestFriend")`

- `let myEmptyDictionary : [String : Int] = Dictionary<String, Int>()`

  Result<success, failure>와 같은 형태

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])