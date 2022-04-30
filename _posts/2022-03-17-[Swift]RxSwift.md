---
title: 'RxSwift 시작하기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["RxSwift", "MVVM"]
---

# RxSwift 시작
![rx](https://user-images.githubusercontent.com/80687913/158733963-bdfd586b-dbf8-4558-95ad-57c1a7a424b1.png)

## 계기
새로 시작하는 프로젝트 CornFarmer가 있다.
협업 프로젝트인데 내가 뒤늦게 참여해서 백엔드와 AOS는 만들어져 있는 상황이었다.
디자이너분께서 추후 디자인을 바꾸실 예정이라고 하셨고 이번에야 말로 MVVM을 사용하기 적합한 상황이라는 생각하에 MVVM을 도입하기로 하였다.

## Reactive Programming
MVC를 도입해 만든 프로젝트 Portfolian은 비동기 처리를 위해 Closure, Delegate, Notification을 사용하였다.
프로젝트를 만들면서 불편했던 점은 일일이 명시해줘야하는 것들이 너무 많다는 점이었다.

클로저를 활용해서 응답 데이터를 받고 UI를 업데이트하는 상황을 가정해보자.
해당 변경사항을 명시해준 뒤, 다시 UI를 업데이트 해야할 것이다. 명시적으로 UI를 한번 더 업데이트 해줘야 한다는 것이다.

### 명령형 프로그래밍
```swift
AlamofireManager.shared.getProfile(userId: userId) { [weak self] (response) in
    guard let self = self else { return }
    self.profile = response
    DispatchQueue.main.async {
        self.tableView.reloadData()
    }
}
```
위와 같은 함수를 reactive하게 바꿔보자.
프로퍼티 옵저버를 활용할 것이다.

### 선언형 프로그래밍
```swift
var profile: Profile {
    didSet {
        self.tableView.reloadData()
    }
}
```
profile이라는 데이터가 바뀌면 UI가 업데이트 되게 된다.

아니 그래서..

---

## RxSwift 란?
Reactive Extensions ReactiveX의 약어이다. Reactive Programming을 좀 더 쉽게 할 수 있도록 도와주는 프레임워크라는 말이다.

우리가 많이 사용하는 Alamofire도 사실 URLSession으로 할 수 있지만 미리 구현되어진 다양한 기능을 사용하면 가독성도 좋아지고 코드의 길이도 짧아지기 때문에 사용하는 것과 같다.

아래는 혹시 궁금한 사람이 있을까봐..

> RxSwift는 코드를 새로운 데이터에 반응하며 순차적으로 처리하게 함으로써 비동기 프로그래밍을 쉽게하도록 도와줍니다.

비동기란 무엇일까?
> 대부분의 Class에서는 비동기로 작업을 수행하고 모든 UI 구성은 기본적으로 비동기로 처리하기 때문에 코드 전체가 어떤 순서로 실행되는지 가정하는 것은 불가능하다.
결국 코드는 사용자 입력, 네트워킹 등 다양한 외부 요인에 따라 다르게 실행된다. 앱을 실행할 때마다 외부 요인에 따라 코드가 완전히 다른 순서로 실행될 수 있다.

# More

이글은 [Zedd0202](https://zeddios.tistory.com/689)님의 글을 참고하였습니다.
