---
title: 'ReactorKit 시작하기'
categories: ['iOS']
post-image: ../assets/images/Apple-iOS.png
tags: ["RxSwift", "MVVM", "Reactor Kit"]
---

# `경고 - 제 주관적인 생각과 이해가 많이 포함되어 있습니다.`

# Reactor Kit 시작
![리액터킷](https://user-images.githubusercontent.com/80687913/166709489-c940bcc4-5599-4ab7-a655-76ef1794ed9e.png)

## Reactor Kit
> ReactorKit은 전수열님이 만드신 프레임워크로, 사용자 인터랙션과 뷰 상태가 관찰 가능한 스트림을 통해 단방향 데이터 흐름을 가진 아키텍처 구조를 가지고 있다. 뷰와 비즈니스 로직을 분리할 수 있게 되면서 모듈간 결합도가 낮아지고 테스트하기 쉬워졌다. 또한, 자칫 복잡해질 수 있는 비동기 코드를 일관되게 작성할 수 있게 되었다.

## 생긴 이유
> MVVM과 함께 RxSwift를 같이 사용했을때 상태값관리가 어렵단 문제점을 발견하고 이를 해결하고자 만들었다고한다.

## 장점
ReactorKit의 장점은

- 테스트: 뷰 컨트롤러가 가벼워지고, 리액터가 뷰에 대한 의존성이 없기 때문에 테스트하기 좋음.
- RxSwift: RxSwift 기반으로 만든 것이기 때문에, RxSwift의 모든 기능을 사용 가능.
- 상태값관리: 데이터가 단방향 흐름이기 때문에, 상태값관리가 편하고, 중간상태를 reduce() 라는 메소드로 관리하기 때문에 상태관리가 간결해짐.
- 코드의 간결: View나 Reactor 프로토콜이 적용되었기 때문에 코드가 깔끔해짐.
- 부담없음: 부분적으로 아키텍처를 적용가능
- 일관적인 형태: 자칫 복잡해질 수 있는 비동기 코드를 일관있게 작성할 수 있음

## 내가 ReactorKit을 시작하게 된 계기
- 다양한 대기업에서 ReactorKit 사용하는데에는 이유가 있을 것이라는 생각.
- 단방향적이고 일관된 코드를 작성하게 되면서 코드를 보다 간결하고 깔끔하게 관리할 수 있지 있을 것이라는 기대.
- 상태값관리에 대한 용이성
- 테스팅을 해보고 싶음

## 데이터 흐름
![데이터 흐름](https://user-images.githubusercontent.com/80687913/166748792-14439098-34a1-4b7f-995e-707fef27b5d8.png)

ReactorKit에는 UI에 해당하는 View와 UI에 반응하여 비즈니스 로직을 처리하는 Reactor로 구성

View는 State만을 표현한다. 뷰 컨트롤러나 셀도 모두 뷰에 해당한다.

View에서는 인터렉터 이벤트들을 Reactor의 Action값으로 넘기고, reactor의 state값을 구독하고 해당 상태에 따라 UI를 업데이트한다.

즉, View는 비즈니스 로직을 수행하지 않는다.

반대로, Reactor는 View의 상태를 관리한다. 

Reactor에 View의 Action을 미리 정의해놓고, 해당 action을 처리하여 다시 View에 State값을 넘기는 것

Reactor는 UI 레이어에서 독립적이기 때문에 비교적 테스트하기 용이하다.

## View

UI가 있고, UI들의 Action을 Reactor에 넘기고, Reactor의 State를 구독하고 있는 형태

View 프로토콜을 적용하면 뷰를 정의할 수 있다. DisposeBag 속성과 bind(reactor:) 메서드를 필수로 정의해야 한다.
```swift
import ReactorKit
import RxSwift

class UserViewController: UIViewController, View {
  var disposeBag = DisposeBag()

    func bind(reactor: UserViewReactor) {
        // Action
        bindAction()
        // State
        bindState()
    }

    private func bindAction(_ reactor: UserViewReactior) {
        self.followButton.rx.tap
            .map { Reactor.Action.follow }
            .bind(to: reactor.action)
            .disposed(by: self.disposeBag)
    }

    private func bindState(_ reactor: UserViewReactior) {
        reactor.state.map { $0.isFollowing }
            .distinctUntilChanged()
            .bind(to: self.followButton.rx.isSelected)
            .disposed(by: self.disposeBag)
    }   
}
```

## Reactor
![View와 Reactor 사이의 데이터 플로우](https://user-images.githubusercontent.com/80687913/166800301-1197e18c-676b-4b4c-b894-3ff0e91f345e.png)

리액터를 정의하기 위해서는 Reactor 프로토콜을 사용한다.

사용자 인터랙션을 표현하는 Action과 뷰의 상태를 표현하는 State, 그리고 상태를 변경하는 가장 작은 단위인 Mutation을 클래스 내부에 필수로 정의해야 한다.

 또한 가장 첫 상태를 나타내는 initialState가 필요하다.

- Action

    - View로부터 받을 Action을 enum으로 정의
- Mutation
    - View로부터 action을 받은 경우, 해야할 작업단위들을 enum으로 정의
- State

    - 현재 상태를 기록하고 있으며, View에서 해당 정보를 사용하여 UI업데이트
- mutate(action:) -> Observable<Mutation>

    - Action이 들어온 경우, 어떤 처리를 할것인지 Mutation에서 정의한 작업 단위들을 사용하여 Observable로 방출
    - Action 스트림을 Mutation 스트림으로 변환하는 역할, 네트워킹이나 비동기로직 등의 사이드 이펙트를 처리
    - [concat, merge, combineLatest, withLatestFrom, zip](https://ios-development.tistory.com/177) 등의 비동기 처리가 유용 
- reduce(state:mutation:) -> State

    - 현재 상태(state)와 작업 단위(mutation)을 받아서, 최종 상태를 반환
    - mutate(action:) -> Observable<Mutation>이 실행된 후 바로 해당 메소드 실행

```swift
import Foundation
import RxSwift
import RxCocoa
import ReactorKit

class UserViewReactor: Reactor {
    let initialState = State()
    
    enum Action {
        case increase
        case decrease
    }
    
    // 처리 단위
    enum Mutation {
        case increaseValue
        case decreaseValue
        case setLoading(Bool)
    }
    
    // 현재 상태를 기록
    struct State {
        var value = 0
        var isLoading = false
    }
    
    // Action이 들어온 경우, 어떤 처리를 할건지 분기
    func mutate(action: Action) -> Observable<Mutation> {
        switch action {
        case .increase:
            return Observable.concat([
                Observable.just(.setLoading(true)),
                Observable.just(.increaseValue).delay(.seconds(1), scheduler: MainScheduler.instance),
                Observable.just(.setLoading(false))
            ])
        case .decrease:
            return Observable.concat([
                Observable.just(.setLoading(true)),
                Observable.just(.decreaseValue).delay(.seconds(1), scheduler: MainScheduler.instance),
                Observable.just(.setLoading(false))
            ])
        }
    }
    
    // 현재 상태와 처리 단위를 받아서 다음 상태를 반환하는 함수
    func reduce(state: State, mutation: Mutation) -> State {
        var newState = state
        switch mutation {
        case .increaseValue:
            newState.value += 1
        case .decreaseValue:
            newState.value -= 1
        case .setLoading(let isLoading):
            newState.isLoading = isLoading
        }
        return newState
    }
}
```

## 테스팅 관련해서는 추후 작성 예정입니다.

## 마무리...

무작정 따라하려다보니 막히는 부분도 많았고 어려웠는데 이번 기회에 방향을 잡을 수 있었다.
이번엔 진전이 꼭 있었으면 좋겠다.

# More

이글은 [전수열](https://medium.com/styleshare/reactorkit-시작하기-c7b52fbb131a), [김종권의 iOS 앱 개발 알아가기](https://ios-development.tistory.com/782)님의 글을 참고하였습니다.
