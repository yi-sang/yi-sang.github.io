---
title: '상속'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 상속

> 자식클래스가 부모클래스로 부터 **기능을 물려받는 것**
>
> - 단일 상속만 가능
>
> - 승계해 주는 클래스: **부모/슈퍼/상위 클래스**
> - 승계 받는 클래스 : **자식/서브/하위 클래스**
> - Overriding (재정의)

```swift
import UIKit
// 슈퍼클래스
class Friend {
 
    var name : String
    
    init(_ name: String){
        self.name = name
    }
    
    func sayHi(){
        print("안녕?! 난 \(self.name) 라고 해")
    }
}

// 서브클래스
class BestFriend : Friend {
  
    // override로 부모의 메소드를 가져왔다.
    override init(_ name: String) {
        // super 로 부모의 메소드 사용(기존의)
        super.init("베프 " + name)
    }
    
    override func sayHi() {
        super.sayHi()
    }
    
    func sayGoodBye(){
        print("sayGoodBye() called")
    }
    
}

let myFriend = Friend("쩡대리")

myFriend.sayHi()

let myBestFriend = BestFriend("영희")

myBestFriend.sayHi()

myBestFriend.name
```

💡 이것 저것 더 공부 해봤는데

override란 다시 정의하겠다!

super란 부모의 구현을 따르겠다!

final로 override를 막을 수 있다!

다른 것들은 일단 훓어보고 넘어간다... 
넘 어려우면 다음에 하기 싫어지므로..

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

[zedd](https://zeddios.tistory.com/386)



