---
title: '객체 생성자, 해제자'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 객체 생성자, 해제자

```swift
import UIKit

class MyFriend {
    
    var name : String
    
    init(_ name: String = "이름없음"){
        self.name = name
        print("init() MyFriend 가 메모리에 올라갔다. - ", self.name)
    }
    
    deinit{
        print("deinit() 메모리에서 사라짐 - ", self.name)
    }
    
    // deinit 검증을 위해 작성
    var calledTimes = 0
    let MAX_TIMES = 5
    
    static var instancesOfSelf = [MyFriend]()
    
    class func destorySelf(object: MyFriend){
        instancesOfSelf = instancesOfSelf.filter{ (aFriend : MyFriend) in
            aFriend !== object
        }
    }
    
    func call(){
        calledTimes += 1
        print("called \(calledTimes)")
        if calledTimes > MAX_TIMES {
            MyFriend.destorySelf(object: self)
        }
    }
    
}

var myFriend = MyFriend("쩡대리")
let aFriend = MyFriend()
// 메모리에 올라감

// Unmanaged.passUnretained(객체).toOpaque()
// 로 해당 객체의 메모리 주소를 프린트 할 수 있습니다.
let anObjectMemoryAddress = Unmanaged.passUnretained(aFriend).toOpaque()
let secondMemorryAddress = Unmanaged.passUnretained(myFriend).toOpaque()

print(anObjectMemoryAddress)
print(secondMemorryAddress)

weak var aFriendToBeDestoried = MyFriend("개발하는 정대리")

if aFriendToBeDestoried != nil {
    aFriendToBeDestoried!.call()
} else {
    print("객체가 더 이상 메모리에 없습니다.")
}

```

💡 뭔가 어려운데 결론은 메모리에서 사라지면 deinit()이 호출된다는 것!

ARC에 대해서는 나중에 더 알아보자!

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])



