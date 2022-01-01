---
title: '매개변수로서 클로저'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# 매개변수로서 클로저

```swift
import UIKit

// (String, String) -> Void
//func completion(first: String, second: String){
//
//}

// 매개변수로서 데이터를 여러개 반환하는 클로저
func sayHiWithFullName(completion: (String, String) -> Void){
    print("sayHiWithFullName() called")
    sleep(2)
    // 클로저를 실행과 동시에 데이터를 반환
    completion("빡코딩", "호롤롤로")
}

sayHiWithFullName { first, second in
    print("첫번째: \(first), 두번째: \(second)")
}

sayHiWithFullName { _, second in
    print("두번째: \(second)")
}

sayHiWithFullName{
    print("첫번째: \($0), 두번째: \($1)")
}

// 컴플리션핸들러가 필요없는 상황이 있을 때
func sayHiOptional(completion: (() -> Void)? = nil){
    print("sayHiOptional() called")
    sleep(2) // 2초 잠깐 멈추기
    // completion 클로저 실행
    completion?()
}

sayHiOptional {

}

sayHiOptional()

sayHiOptional(completion: {
    print("2초가 지났다.!!")
})

// (Int) -> String
func transform(number: Int) -> String {
    return "숫자 : \(number)"
}

var myNumbers : [Int] = [0, 1, 2, 3, 4, 5]

var transformedNumbers = myNumbers.map { aNumber in
    return "숫자: \(aNumber)"
}

var transformedNumbers = myNumbers.map { (aNumber: Int) -> String in
    return "숫자: \(aNumber)"
}

var transformedNumbers = myNumbers.map {
    return "숫자: \($0)"
}

//var transformedNumbers11 = myNumbers.map
```

💡 점점 정리할게 적어지는 걸봐선 실력이 아직 많이 부족하다는 걸 느꼈다.

```swift
func sayHiOptional(completion: (() -> Void)? = nil){
    print("sayHiOptional() called")
    sleep(2) // 2초 잠깐 멈추기
    // completion 클로저 실행
    completion?()
}

sayHiOptional {

}

sayHiOptional()

sayHiOptional(completion: {
    print("2초가 지났다.!!")
})
```

@escaping 이 있을 때는 사용할 수 없다.

이런 게 필요했어 ㅠ

탈출 클로저에 대해서도 공부했는데 

**탈출 클로저로 만들어 주면** 

**1. 해당 클로저를 외부 변수/상수에 저장이 가능하고**

**2. 해당 함수가 실행이 끝나도 클로저 실행이 가능하다.**

서버와 통신에 있어서 이미지와 같은 데이터가 큰 파일을 받을 때 비동기 방식으로 코드를 처리하는데 작업 순서를 정해두지 않으면 데이터를 받아오기도 전에 사용하게 되는 문제가 발생할 수 있기 때문에 이러한 경우에는 탈출 클로저를 사용한다.

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])



