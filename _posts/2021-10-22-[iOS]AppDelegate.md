---
title: '앱델리게이트'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']
---

# AppDelegate와 Scene Delegate

AppDelegate.swift의 역할은

**iOS 13** 전 후로 나눌 수 있다. 

iOS 13 이전 버전에서 app delegate가 앱의 실행과 포그라운드, 백그라운드에 대한 로직을 처리하는 역할을

iOS 13 이후 버전에서 Scene Delegate가 생겨나면서 넘겨주었습니다.

## iOS 13 이전 버전

-   AppDelegate

    

    -   Process Lifecycle

        

        -   App Launched
        -   App Terminated

    

    -   UI Lifecycle

        

        -   Entered Foreground
        -   Became active

iOS 13 전에는 앱은 오직 "하나의 프로세스"와 그에 맞는 "하나의 UI"만 가지기 때문에 문제될 것이 없었지만

iPad에서 **multi window**를 지원하면서 앱은 하나의 프로세스만을 공유하지만 여러 UI 인스턴스 또는 Scene session이 있을 수 있게 되었습니다.

캘린더앱을 예로 들면 년을 나타내는 UI인스턴스, 월을 나타내는 UI인스턴스, 일을 나타내는 UI인스턴스등으로 나뉘질 수 있습니다.

![image](https://user-images.githubusercontent.com/80687913/138281311-a8064c0a-541e-4bd9-9700-39e5c15e4f3a.png)

이는 App delegate의 역할이 변경되어야 함을 의미합니다.

프로세스 이벤트 및 Lifecycle에는 여전히 AppDelegate가 책임을 가지지만 

더이상 UI Lifecycle과는 관련된것이 없기 때문입니다. 이 역할은 SceneDelegate에게 넘겨주게 되었습니다,

## **iOS 13 이후 버전**

-   AppDelegate

    -   Process Lifecycle

    -   Session Lifecycle

        

        -   Session Created

        -   Session Discarded

            

-   SceneDelegate
    
    -   UI Lifecycle
        
        
        
        -   Entered Foreground
        -   Become active

---

또한,  iOS13 이후 버전의 앱에서는 Session Lifecycle에 대한 역할이 추가되었는데 새로운 Scene Session이 생성되거나, 기존 Scene Session이 삭제될 때 시스템이 AppDelegate에게 알리게 됩니다.

## 앱 델리게이트의 역할

1.  앱의 중요 데이터 구조를 초기화
2.  앱의 scene의 환경설정 (Configure)
3.  앱 밖에서 발생한 알림(배터리 부족 경고, 다운로드 완료 알림 등)에 대응
4.  특정한 scenes, views, view controllers에 국한하지 않고 앱 자체를 타겟하는 이벤트에 대응
5.  애플 푸쉬 알림과 같이 실행시 요구되는 모든 서비스를 등록



## 앱 델리게이트 메서드의 역할

-   **func** application(_:didFinishLaunchingWithOptions:)

    **앱이 실행되었을 때 최초 1회 발생하는 함수** 

-   **func** applicationDidBecomeActive(**_** application: UIApplication)

    **background > foreground로 진입한 이후 발생,** 

-    **func** applicationWillResignActive(**_** application: UIApplication) 

     **foreground > background로 진입할 때 발생.**

-    **func** application(**_** application: UIApplication, didReceiveRemoteNotification userInfo: [AnyHashable: **Any**], fetchCompletionHandler completionHandler: **@escaping** (UIBackgroundFetchResult) -> Void)

     **Push알림을 받고 탭해서 앱으로 진입했을 때 payload를 핸들링하는 함수**



>   iOS 13이후에는 SceneDelegate를 사용할 수 있다. 이는 햐나의 앱이 여러개의 UI를 띄울 수 있게 되면서, 이 UI가 별도의 생명주기를 가질 필요가 생겼기 때문으로 기존 AppDelegate가 수행했던 생명주기 관리의 많은 부분이 SceneDelegate로 옮겨가게 되었다. 여기서 AppDelegate는 앱의 초기 구동과 앱 전체에 관련된 이벤트의 처리정도 만을 담당하도록 기능이 축소되었다. 
>   iOS 12 이하의 경우에는 여전히 생명주기 관리에 AppDelegate를 사용하며, iOS 13 이상이더라도 Scene을 지원하지 않게 만들었다면 여전히 AppDelegate를 사용한다.

Scene을 지원하지 않는 경우, 모든 생명주기 관련 이벤트들은 appDelegate에 전달된다. appDelegate객체는 앱의 모든 window를 관리하기 때문에 앱의 상태 변화는 앱의 모든 UI에 영향을 미친다.

# More

[자세한 설명](https://zeddios.tistory.com/811)