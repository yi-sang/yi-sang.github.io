---
title: 'iOS 면접 질문 및 답변 정리'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기']
---

하루 두개씩 올리던 글을 잠시 멈추고 잘 정리 되어진 [🔥추천 iOS면접 질문 총 정리](https://velog.io/@grap_ios/iOS-Swift-면접-준비) 을 참고해서 공부해야겠다.

# What is Cocoa and Cocoa Touch?

| **Cocoa**                                                    | **Cocoa Touch**                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. OS X용 애플리케이션 개발 환경                             | 1. iOS용 애플리케이션 개발 환경                              |
| 2. Foundation 및 AppKit 프레임워크 포함                      | 2. Foundation 및 UIKit 프레임워크 포함                       |
| 3. Objective-C 런타임을 기반으로 하고 루트 클래스에서 상속되는 모든 클래스/객체를 참조하는 데 사용된다. | 3. 프로그래밍 방식의 인터페이스를 사용하여 애플리케이션 개발을 참조하는 데 사용된다. |

## Which JSON framework is supported by iOS? 

-   iOS는 SBJson 프레임워크를 지원합니다.

-   SBJson은 Objective-C용 JSON 파서(문장의 구조 분석, 오류 점검 프로그램) 및 생성기이다.
-   유연한 API 및 추가 제어를 제공하여 JSON 처리를 더 쉽게 만든다.

## Differentiate ‘app ID’ from ‘bundle ID’. Explain why they are used.

[App ID]는 단일 개발 팀에서 하나 이상의 앱을 식별하는 데 사용되는 두 부분으로 구성된 문자열이다. 앱 Group ID라고 생각하면 된다. 이 AppID는 한번 등록하면 삭제, 리네임, 수정 절대 불가능하다. 한번 등록하면 본인의 계정에서 평생 봐야 한다. 문자열은 팀 ID와 번들 ID 검색 문자열로 구성되며 두 부분을 구분하는 마침표(.)가 있다. 팀 ID는 Apple에서 제공하며 특정 개발 팀에 고유한 반면 번들 ID 검색 문자열은 단일 앱의 번들 ID 또는 앱 그룹의 번들 ID 집합과 일치하도록 개발자에 의해 제공된다.

AppID에서는 번들Seed ID + 번들ID

 예) BAM91AC832.kr.co.mysite.* 

1)   prefix  :  예) BAM91AC832 / uniqueness를 만들기위해 프로비저닝 포털에서 생성해준 것 이다.

​           이것은 번들 Seed ID라고 부른다.

2)   body  :  예) kr.co.mysite / 이게 젤 중요합니다. 이게 일종의 Group Id이다. 

3)   suffix  :  여기서는 * 로 지정하고 나중에  각 앱의 Project Name으로 대체한다.

번들 ID는 각 앱을 정의하며 Xcode로 지정된다. 단일 Xcode 프로젝트는 여러 대상을 가질 수 있으므로 여러 앱을 출력할 수 있다. 일반적인 사용 사례는 lite/free 버전과 pro/full 버전을 모두 갖거나 여러 가지 방법으로 브랜드가 지정된 앱이다.

 예) kr.co.mysite.myApp1 

1)   prefix  :  예) BAM91AC832 / 이게 사라진다.

2)   body  :  예) kr.co.mysite / 이것 그대로 유지된다. 

3)   suffix  : *  ==> Project Name 으로 지정한다. 

## Which are the ways of achieving concurrency in iOS?

iOS에서 동시성을 달성하는 세 가지 방법은 다음과 같다.

-   Threads
-   Dispatch queues
-   Operation queues

## Explain the different types of iOS Application States.

다양한 iOS 애플리케이션 state는:

-   **Not running** state: 앱이 실행되지 않았거나 실행 중이었으나 시스템에 의해 종료된 경우이다.
-   **Inactive** state: 앱이 포그라운드에서 실행 중이지만 현재 이벤트를 수신하지 않는 경우. 앱은 다른 상태로 전환될 때 잠시 이 상태를 유지한다. 비활성 상태로 유지되는 유일한 시간은 사용자가 화면을 잠그거나 시스템이 전화 또는 SMS 메시지와 같은 일부 이벤트에 응답하도록 사용자에게 프롬프트할 때이다.
-   **Active** state: 앱이 포그라운드에서 실행 중이고 이벤트를 수신 중일 때. 포그라운드 앱의 일반 모드이다.
-   **Background** state: 앱이 백그라운드에서 코드를 실행 중일 때. 대부분의 앱은 일시 중단되는 도중 잠시 이 상태에 들어간다. 그러나 추가 실행 시간을 요청하는 앱은 일정 시간 동안 이 상태를 유지할 수 있습니다. 또한 백그라운드로 직접 실행되는 앱은 비활성 상태가 아닌 이 상태로 들어간다.
-   **Suspended** state: 일시 중단된 앱은 메모리에 남아 있지만 코드를 실행하지 않습니다. 메모리 부족 상태가 발생하면 시스템은 포그라운드 앱을 위한 더 많은 공간을 확보하기 위해 예고 없이 일시 중단된 앱을 제거할 수 있다.

## Which is the framework that is used to construct an application’s user interface for iOS?

UIKit 프레임워크, UIKit 프레임워크는 iOS용 애플리케이션의 사용자 인터페이스를 개발하는 데 사용됩니다. 이벤트 처리, 드로잉 모델, 창, 보기 및 터치 스크린 인터페이스용으로 특별히 설계된 컨트롤을 제공한다.

## Which is the application thread from where UIKit classes should be used? 

UIKit 클래스는 애플리케이션의 메인 스레드에서만 사용해야 한다.

## Which API would you use to write test scripts to exercise the application’s UI elements?

UI 자동화 API, UI 자동화 API는 테스트 절차를 자동화하는 데 사용됩니다. UI 자동화 API에 작성된 JavaScript 테스트 스크립트는 애플리케이션과의 사용자 상호 작용을 시뮬레이션하고 호스트 컴퓨터에 로그 정보를 반환한다.

## When would you say that an app is not in a running state?

다음과 같은 경우 앱이 '실행되지 않음' 상태라고 한다.
– 실행되지 않을 때.
– 실행 중 시스템에 의해 종료된 경우.

## When is an app said to be in active state? 

앱은 포그라운드에서 실행 중이고 이벤트를 수신할 때 활성 상태에 있다고 합니다.

## 12. Which are the app’s state transitions when it is launched?

앱은 실행되기 전에 not running state라고 합니다.

잠시 inactive state를 전환한 후 실행 시 active 또는 background state로 이동한다.

## Which is the state an app reaches briefly on its way to being suspended?

앱이 일시 중단되는 도중 잠시 백그라운드 상태가 된다.

## What is Swift and what is Objective-C?

Objective-C는 OS X 및 iOS용 소프트웨어를 작성하는 데 사용하는 기본 프로그래밍 언어입니다. C 프로그래밍 언어의 상위 집합이며 개체 지향 기능과 동적 런타임을 제공한다. Objective-C는 C의 구문, 기본 유형 및 흐름 제어 문을 상속하고 클래스 및 메서드를 정의하기 위한 구문을 추가한다. 또한 객체 그래프 관리 및 객체 리터럴에 대한 언어 수준 지원을 추가하는 동시에 동적 타이핑 및 바인딩을 제공하여 런타임까지 많은 책임을 연기한다.

Swift는 iOS, OS X, watchOS 및 tvOS 앱을 위한 새로운 프로그래밍 언어로 C 호환성의 제약 없이 C 및 Objective-C의 장점을 최대한 활용한다. Swift는 안전한 프로그래밍 패턴을 채택하고 최신 기능을 추가하여 프로그래밍을 더 쉽고 유연하고 재미있게 만든다. Swift는 Objective-C 개발자에게 친숙하고 새로운 프로그래머에게 친숙하다.

## What is SpriteKit and what is SceneKit?

SpriteKit은 애니메이션 2D 개체를 쉽게 개발할 수 있는 프레임워크이다.

SceneKit은 3D 그래픽 렌더링을 지원하는 OS X에서 상속된 프레임워크이다.

SpriteKit, SceneKit 및 Metal은 iOS 기기의 강력한 GPU가 제공할 수 있는 것을 재정의하는 차세대 모바일 게임을 구동할 것으로 예상된다.

## What are iBeacons?

iBeacon.com은 iBeacon을 모바일 앱이 물리적 세계에서 비콘의 신호를 듣고 그에 따라 반응할 수 있도록 하는 Apple의 기술 표준으로 정의한다. iBeacon 기술을 통해 모바일 앱은 마이크로 로컬 규모에서 위치를 이해하고 위치를 기반으로 사용자에게 하이퍼 컨텍스트 콘텐츠를 제공할 수 있다. 기본 통신 기술은 Bluetooth Low Energy이다.

## What are layer objects?

layer 개체는 시각적 콘텐츠를 나타내는 데이터 개체이며 뷰에서 콘텐츠를 렌더링하는 데 사용됩니다. 사용자 지정 계층 개체를 인터페이스에 추가하여 복잡한 애니메이션 및 기타 유형의 정교한 시각적 효과를 구현할 수도 있습니다.

## Outline the class hierarchy for a UIButton until NSObject.

UIButton은 UIControl에서 상속하고, UIControl은 UIView에서 상속하며, UIView는 UIResponder에서 상속하고, UIResponder는 루트 클래스 NSObject에서 상속합니다.



---

---



# More

[참고 링크1](https://www.edureka.co/blog/interview-questions/ios-interview-questions/)

[참고 링크2](https://memohg.tistory.com/124#%23%20Stack)

[iOS면접 질문](https://github.com/odong-Tree/iOSInterviewquestions)

[iOS면접 질문 정리](https://haningya.tistory.com/217)

[iOS면접 질문 깃허브](https://github.com/Sueaty/iOS-Interview-KR)

