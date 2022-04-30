---
title: 'iOS Architecture'
categories: ['iOS']
post-image: ../assets/images/Swift-Logo.png
tags: ["MVC", "MVVM", "MVP", "Architecture", "Design Pattern"]
---
# `경고 - 제 주관적인 생각과 이해가 많이 포함되어 있습니다.`
# iOS Architecture
## 개요
깃허브에 공개된 여러 프로젝트들을 보면서 MVVM패턴에 대해서 공부를 하는데 정말 쉽지 않았다.
MVC, MVP, MVVM 대해 제대로된 이해가 없이 무작정 해보려고 한 결과라고 생각이 들었고
이번 기회에 애플의 디자인 패턴에 대해서 제대로 공부하고 넘어가야겠다는 생각을 했다.

## Architecture
우선 소프트웨어 아키텍쳐에 대해 알아야했다.
소프트웨어 아키텍쳐는 시스템을 구성하는 서브 시스템, 컴포넌트, 모듈과 같이 구성요소 간의 관계를 관리하는 시스템의 **구조**이다.

## Design Pattern
다음으로는 디자인 패턴에 대해 알아야했다.
디자인 패턴은 프로그램 개발 과정 속에서 자주 나타나는 문제들을 쉽게 해결하기 위한 **방법**으로 과거의 소프트웨어 개발 과정에서 발견된 설계의 노하우를 바탕으로 이후에도 재사용할 수 있기 좋은 형태로 가공하여 정리한 것 이다.

## Architecture vs Design Pattern
**소프트웨어 아키텍처**는 프로그램 내에서 큰 구조로 구성되어 다른 구성 요소들을 관리하는 역할을 한다. 반면에 **디자인 패턴**은 특정 유형의 문제를 해결하는 방법이다.

즉 우리가 부르는 디자인 패턴이란 잘 설계된 소프트웨어 아키텍쳐를 패턴화 시킨 것을 의미한다.
아키텍쳐 디자인 패턴을 디자인 패턴으로 줄여불렀던 것이다.

---
구조를 생각하지 않고 프로그램을 작성한다고 프로그램이 돌아가지 않는 것은 아니다. 하지만 가독성과 유지보수, 테스팅에 어려움을 겪을 것이다. 회사 입장에서는 아키텍쳐를 잘 해놓으면 추후 상당히 많은 이익을 얻을 수 있는 것이다.
물론 정답은 없다. 프로젝트의 성격과 특성에 맞는 아키텍쳐를 선정하고 잘 활용한다면 그게 제일 맞는 아키텍쳐가 되는 것이다.

하지만 좋은 아키텍쳐의 기준과 특징은 있다.
### 아키텍쳐의 기준과 특징
1. 균형잡힌 분배
각 클래스가 독립적인지, 각 객체의 역할이 확실하며 균형 잡혀서 분배되어있어야한다.

2. 테스트
테스팅을 할 수 있는지, 가령 서버가 점검 중일 때 서버가 없이도 테스팅할 수 있는 **구조**라면 좋은 아키텍쳐일 것이다.

3. 사용성
사용하기 쉬워야할 것이다.

4. 단방향성의 데이터 흐름
단순한 데이터 흐름은 코드를 쉽게 이해할 수 있게 해주며 쉬운 디버깅을 제공한다.
데이터를 운용하면서 여러 객체들을 오가거나 싱글톤 패턴을 남용한다면 에러가 발생했을 때 원인을 찾기 힘들어진다.

좋은 아키텍쳐를 만들기 위해서는,
테스트를 고려하여 균형잡힌 분배를 해야할 것이고 잘 분배가 되어야할 것이다.
사용하기 쉽다면 더 좋을 것이고,
싱글톤 사용을 지양하고 Reactorkit과 같은 라이브러리를 함께 사용한다면 단방향적인 구현이 가능해질 것이다.

균형잡힌 분배를 하고 싶은데 어떻게 해야할 까?
디자인 패턴을 이용하자.
우리와 같은 시행착오를 겪은 선배 개발자들은 크게 세가지 카테고리로 분해해왔다.
Model, View, [Controller, Presenter, ViewModel] 
Model: 프로그램에서 사용되는 데이터들의 묶음
View: 시각적인 부분으로 UI에 해당
Controller, Presenter, ViewModel: Model과 View 사이의 중재자로 크게 View를 통해 입력되는 터치와 제스처같은 사용자의 액션을 다루고 이에 따른 Model의 값의 조정을 요청하고  Model의 변화에 맞게 View 을 갱신하는 역할

---
## MVC
- M: Model
- V: View
- C: Controller

가장 자연스러운 방식의 아키텍쳐이다.
일반적으로 설명되는 MVC는 다음과 같다.
### 전통적인 방식의 MVC
![image](https://user-images.githubusercontent.com/80687913/166102240-7866ecdf-aab4-4188-a51a-e160589aab15.png)
위의 다이어그램을 통해 우리는 Model, View, Controller 이 세 요소가 강하게 연결되어 있음을 알 수 있다. View는 사용자의 액션을 Controller에게 전달하고 Controller는 이에 따른 데이터의 갱신을 Model에게 요청한다. 이렇게 Model에서 데이터의 갱신이 일어나고 Model은 이런 상태를 View에게 전달한다. 그렇게 되면 View역시 갱신된 데이터에 맞게 갱신된다.

위와 같은 방식은 [1. 균형잡힌 분배](#아키텍쳐의-기준과-특징)에서의 각 클래스는 독립적이어야한다는 조건에 맞지 않고 각각의 재사용성은 떨어진다.

이에 애플은 새로운 MVC 아키텍쳐를 제시하였다.

### Cocoa MVC
애플의 MVC에 대해 알아보자
![image](https://user-images.githubusercontent.com/80687913/166102256-855b4a9a-d1e5-4fb3-af49-db9d1183cc81.png)

Controller는 View와 Model의 중재자로 View와 Model의 직접적인 연결을 막는다. -> 독립성 보장

하지만 실제 개발에서는 Controller의 역할을 UIViewController가 담당하게 되고 UIViewController에서 View를 소유하기 때문에 View Life Cycle에 의해 강하게 연결되어지고, 이는 View와 Controller의 분리를 쉽지 않게하고 고로 View, Controller의 재사용이 어려워지게 된다.

결국 애플이 제시한 MVC와 실제 개발에서의 MVC에는 다소 거리가 있는 것이다. 
모듈끼리 독립적이지 못하다는 것은 테스팅 또한 어렵게 만든다. 실제 독립적인 것은 Model이 전부이다.
UIViewController에서 일어나는 각종 행위(네트워크 통신, Delegation, Notification), UI, 액션 등의 코드로 인해 UIViewController는 방대해지게 되고 Massive ViewController라는 별명을 갖게 되었다.

### 실제 개발에서의 MVC
![image](https://user-images.githubusercontent.com/80687913/166104819-ea4f77d5-a455-4c68-93cc-fa8780681dc5.png)

이거다. 내가 개발해왔던 다이어그램. 항상 Cocoa MVC의 그림을 보며 왜 내 코드는 이렇지 않지 라는 생각을 해왔는데 역시나 차이가 있었다.

MVC는 위의 [아키텍쳐의 기준과 특징](#아키텍쳐의-기준과-특징)에 얼마나 부합할까?

1. 균형적인 분배
View와 Model은 확실히 분리되어있다.
하지만 View와 Controller는 강하게 연결되어있다.
2. 테스트
View와 Controller가 강하게 연결되어 있기 때문에 Model로만 테스트를 진행할 수 있다.
3. 사용성
여러 아키텍쳐 중 가장 적은 코드를 필요로 하며 가장 친숙한 아키텍쳐 패턴으로 많은 경험이 없는 개발자들도 쉽게 유지 보수할 수 있다. (유지보수에 유리하다는 뜻은 아니다.)

---

## MVP
- M: Model
- V: View (UIView / UIViewController)
- P: Presenter

![image](https://user-images.githubusercontent.com/80687913/166106964-b11508c8-f63f-406d-a76b-0bbdb4b1f915.png)

위의 [Cocoa MVC](#Cocoa-MVC)와 상당히 유사한 형태를 하고 있다. 실제롣 그럴까?
그렇지 않다
Cocoa MVC에서 UIViewController는 Controller에 해당하고 View와 강하게 연결되어 있었다. 하지만 MVP에서는 UIView나 UIViewController모두 View에 해당한다. 대신 MVP패턴에서는 Presenter라는 것이 등장한다.

Presentersms Cocoa MVC와 는 다르게 View의 Life Cycle에 영향을 받지 않고 레이아웃 코드 역시 Presenter에 존재하지 않는다. 하지만 Controller의 역할(View의 데이터와 상태에 맞추어 갱신하는 역할)을 갖게 된다. Presenter는 Model로 부터 갱신된 데이터를 받아와 뷰를 갱신하는 역할을 한다.

Presenter과 View가 분리 되어 있기 때문에 이는 테스트 효과를 높일 수 있다. 

MVP에서 View는 Presenter를 소유하고 있어야 하고 Presenter는 유저 액션, 데이터 갱신, 상태 갱신에 따라 View를 갱신해주어야 한다.
이를 코드로써 구현할 때 View는 Presenter를 강한 참조로 소유하고 있고 Presenter는 약한 참조로 View를 단순히 가리키고만 있다. 그렇기 때문에 View의 Life Cycle의 영향과 UI와 액션 코드가 공존하는 등의 의존성에서는 벗어날 수 있지만 **참조**에 의한 1:1 의존성에서는 벗어날 수 없다는 한계가 존재한다.

MVP는 위의 [아키텍쳐의 기준과 특징](#아키텍쳐의-기준과-특징)에 얼마나 부합할까?

Distribution : 전통적인 MVC에서 발생한 Model과 View의 의존성 문제는 해결하였다.
하지만 참조에 의한 View와 Controller의 의존성은 존재하지만 비교적 셋 모두 역할별로 적절히 나누어져 있다고 말할 수 있다.

Testability : 각각의 요소를 독립적으로 테스트하기 용이하다.

Easy of Use : Presenter의 추가와 이를 구현하기 위한 프로토콜등의 추가로 코드가 MVC보다 길어진다.

---

## MVVM
- M : Model
- V : View
- VM : ViewModel
![image](https://user-images.githubusercontent.com/80687913/166107884-a791ba64-df2e-4f0c-b781-143fd9d503ac.png)

MVVM의 정의에 의하면 View는 오직 시각적인 요소로만 이루어져야 한다.
View에서는 레이아웃, 애니매이션 그리고 UI 요소들에 대한 초기화 작업 코드들만이 위치하게 된다. 다음으로 ViewModel은 View와 Model 사이에 위치하게 된다. ViewModel은 View의 각 UI 요소들에 대한 인터페이스를 제공합니다. View의 UI 요소들과 ViewModel의 인터페이스를 연결시키는 작업을 "바인딩(Binding)" 이라고 합니다.

(위의 인터페이스란 말은 청사진을 말한다.
즉, 밑그림만 잇는 기본 설계도를 말한다.)

네트워크 등을 이용해서 받아온 Model의 형태를 View의 각 UI요소에 맞는 형태(Ready-To-Display Property)로 바꿔주는 작업을 ViewModel에서 하게 된다.
예를 들어 Model에서 받아온 Date를 String으로 변환하는 작업을 하게 되고 View는 이에 맞춰 갱신이 일어나게 된다.
즉 View의 비즈니스 로직에 대해 테스팅이 가능해진다.

MVP와 마찬가지로 UIView와 UIViewController를 View로 묶어 분류한다.
View에서 해야할 작업은

1. UI 구성요소들을 생성, 레이아웃, 표시(initiate/layout/present)

2. UI 구성요소들을 뷰 모델과 데이터 바인딩

ViewModel에서는 다음과 같은 작업을 해주면 된다.

1. 페이징, 에러처리 등과 같은 로직 작성

2. 사용자에게 UI를 표시하는 로직(Modal로 보여줄지 Alert으로 보여줄지 등)을 작성하고 뷰의 인터페이스를 제공

### MVVM의 단점
물론 MVVM이 완벽하다고 볼 수 없다.
그 이유로는 ViewModel에서 너무 많은 일들을 한다는 점이 지적되고 있다.
이를 해결하기 위해 Builder나 Router의 개념이 도입되고 있다.

---
## 끝으로..
아키텍쳐에 대해 간단히 알아보았다.
디자인 패턴은 아키텍쳐 디자인 패턴을 줄여 말한 것이고 아키텍쳐 패턴이라고 부를 수 있다는 것을 알았다. 또한 좋은 아키텍쳐의 기준과 특징에 대해서도 배웠다.

근데 MVVM하면 항상 따라다니는 이 이름. RxSwift는 뭔데?
### 이어지는 글 [RxSwift 시작하기](https://yi-sang.github.io/blog/Swift-RxSwift)
---
위의 내용은 [protocorn93님의 글](https://github.com/protocorn93/iOS-Architecture) 을 참고하였습니다.







