---
title: '앱이 In-Active 상태가 되는 시나리오'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']

---

# 앱이 In-Active 상태가 되는 시나리오

## iOS Application State Changes

![image](https://user-images.githubusercontent.com/80687913/138757580-f413d013-9d38-4c64-898c-e2b5d8c61f71.png)

앱의 상태 변화



<img width="703" alt="image" src="https://user-images.githubusercontent.com/80687913/138759882-aef4bf80-9397-41f6-aae4-3a9978bfefed.png">

-   Not running(Unattached): 앱이 실행되지 않았거나 시스템에서 종료됨

    -> `application(_willFinishLaunchingWithOptions:)` 앱 실행을 준비하는 메소드

    -> `applicationDidFinishLaunching(_:)` 주로 초기화 코드

    -> `applicationWIllTerminate(_:)` 앱이 종료되기 직전에 호출

-   Foreground:

    -   In-Active: 앱이 Foreground에서 실행중이지만, 이벤트를 받을 수 없음 > 이 상태에 잠시 머물다가 다른 상태로 전이됨

        -> `sceneWillEnterForeground(_:)` 앱이 백그라운드나 낫러닝에서 포어그라운드로 들어가기 직전에 호출된다.

    -   Active: 앱이 화면에 떠 있을 때의 상태 > 이벤트를 받을 수 있음

        -> `sceneWillResignActive(_:) ` 앱이 비활성상태에서 활성상태로 진입하고 난 직후

-   Background: 앱이 백그라운드에서 코드를 실행중. 대부분의 앱은 일시중지 상태로 잠시 이 상태가 된다. 그러나 추가 시간을 요청하는 앱은 일정기간 동안 이 상태로 남아있을 수 있다. 또한 백그라운드로 직접 실행되는 앱은 비활성 상태 대신 이 상태로 전환된다

    -   ->  `sceneDidEnterBackground(_:)` 앱이 백그라운드 상태로 들어갔을 때

-   Suspended: 앱이 백그라운드에 있지만 코드를 실행하지 않음. 시스템은 앱을 자동으로 이 상태로 이동시키고 그렇게 하기 전에 앱에 알리지 않는다. 일시 중지 된 앱은 메모리에 남아는 있지만 코드는 실행되지 않는다. 메모리 부족상태가 발생하면 시스템은 예고없이 일시 중단 된 앱을 제거하여 메모리를 확보한다.

    -   -> 따로 호출되는 메소드는 없다.

사용자나 시스템이 새로운 scene을 만들어달라고 요청하면, UIKit는 이를 만들어 unattached 상태로 만든다. 사용자가 요청한 scene은 곧장 Foreground inactive 상태를 거쳐 active 상태가 되고, 시스템이 요청한 scene은 보통 Background 상태가 되어 이벤트를 처리한 뒤에 Foreground로 올라온다. 사용자가 앱의 UI를 닫게 되면, 해당하는 scene은 UIKit에 의해 Background 상태로 갔다가 Suspended 상태가 된다. UIKit는 언제든지 이 Background나 Suspended 상태인 scene을 회수해 unattached 상태로 되돌려 놓을 수 있다.

### View Controller Life Cycle

앱의 라이프사이클은 앱을 터치해서 실행시키고 완전히 종료되기 까지 아래 단계로 요약 해볼 수 있다.

1.  main 함수 실행
2.  main 함수는 UIApplicationMain 함수를 호출
3.  UIApplicationMain함수는 앱의 본체에 해당하는 객체인 UIApplication 객체를 생성
4.  nib 파일을 사용하는 경우나, Info.plist 파일을 읽어들여 파일에 기록된 정보를 참고해 그 외에 필요한 데이터를 로드
5.  App Delegate 객체를 만들고 앱 객체와 연결해 Main를 만드는 등 실행에 필요한 준비
6.  실행 완료를 앞두고 앱 객체가 App Delegate에게 application:didFinishLaunchingWithOptions: 메시지를 보냄

## 앱이 In-Active 상태가 되는 시나리오를 설명해보자

사용자의 동작에 따라 앱의 상태가 변경된다.

1.  사용자가 앱을 실행한다: Not running » In-Active » Active
2.  앱 실행 도중 홈버튼을 누른다: Active » In-Active » Background
3.  앱을 다시 켠다: Background » In-Active >> Active
4.  앱이 백그라운에 있다가 Suspended 상태로 전이: Active » In-Active » Background » Suspended

**메소드 순서**

**not running 상태에서 앱 실행하고 포어그라운드 직전에 [applicationDidFinishLaunching(_:)](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623053-applicationdidfinishlaunching) 이 호출되고**

**이제 포어그라운드에 진입할 때 [sceneWillEnterForeground(_:)](https://developer.apple.com/documentation/uikit/uiscenedelegate/3197918-scenewillenterforeground) 가 호출되면서 인액티브 상태가 된다.**

**또한 유저가 백그라운드에 진입했을때 [sceneDidEnterBackground(_:)](https://developer.apple.com/documentation/uikit/uiscenedelegate/3197917-scenedidenterbackground?language=objc) 가 호출되고** 

**다시 포어그라운드에 들어가게 될 때 sceneDidBecomeActive(_:) 이 호출되는데 여기서 인액티브 상태를 거쳐가게 된다.**



가장 흔한 예시는 우리가 문자를 공유하기 하려할 때 카카오톡 앱이 실행되는데, 이때 메시지 앱은 In-Active 상태가 되어진다.

## MORE

[자세한 설명](https://fomaios.tistory.com/entry/앱-생명주기App-LifeCycle-1)