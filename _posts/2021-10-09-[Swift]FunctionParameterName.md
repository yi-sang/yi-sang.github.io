---
title: '함수 매개변수 이름'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 함수 매개변수 이름

```swift
import UIKit


// 함수, 메소드 정의
func myFunction(name: String) -> String{
    return "안녕하세요?! \(name) 입니다!"
}

// 함수, 메소드를 호출한다. call
myFunction(name: "쩡대리")


// 함수, 메소드 정의
func myFunctionSecond(with name: String) -> String{
    return "안녕하세요?! \(name) 입니다!"
}

myFunctionSecond(with: "호롤롤로")


// 함수, 메소드 정의
func myFunctionThird(_ name: String) -> String{
    return "안녕하세요?! \(name) 입니다!"
}

myFunctionThird("하하하하")
```

💡 내부에서 동작할 때의 맞는 이름과 외부에서 동작할 때(사용자가 사용할 때)의 적합한 이름이 있을 때가 있다.

근데 하다보면 하나하나 신경쓰기가 어렵다. 개발할 때 뭔가 착착착 하기가 어렵다.

그냥 뭘 하고 싶다. 뭘 만진다. 안 되면 찾아본다 의 반복이라고 해야하나

말로 표현하기 어려운데 뭔가 막무가내로 하다보니 코드도 복잡해지고 지금 당장은 동작할지몰라도 깔끔하지 않다.

함수 형 프로그래밍 관련된 책이라도 읽어봐야할까.

모든 게 확고하지 않다. 오늘 생각한 결론이 내일 다시 생각하면 정반대의 결론이 나온다.

이런 걸 의욕만 넘친다고 해야할까?

할 수 있는 건 화이팅!



# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

