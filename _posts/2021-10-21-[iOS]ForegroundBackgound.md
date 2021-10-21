---
title: '앱이 foreground에 있을 때와 background에 있을 때의 제약사항'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']
---

# 앱이 foreground에 있을 때와 background에 있을 때의 제약사항

-   Foreground mode는 **메모리 및 기타 시스템 리소스에 높은 우선순위**를 가지며 시스템은 이러한 리소스를 사용할 수 있도록 필요에 따라 background 앱을 종료합니다.
-   Background mode는 **가능한 적은 메모리공간을 사용**해야함(시스템 리소스 해제, 메모리에서 해제 후 데이터를 디스크에 작성) 사용자 이벤트를 받기 어렵고 공유 시스템 리소스를 해제하고 이미지 객체 참조 등 메모리 제한

  

UIKit App 상태는 다음과 같이 나눠집니다.

![1*QW4wCQMLo8wUDLBBAd-mwA](https://user-images.githubusercontent.com/80687913/138248442-291bdc29-c80f-4f1d-b9aa-cca4e9555ace.jpeg)

-   **Not Running** : 앱이 System에 의해 종료되거나 실행되지 않은 상태

-   **Foreground상태** : APP이 실행되어 사용자에게 보여지고 있는 상태
    -   오직 하나의 App만 Foreground 상태를 가지며 Inactive, Active 상태로 나뉘어집니다.
        -   **Inactive** 앱이 실행중이지만 아직 아무런 이벤트를 받지 않은 상태 (Foreground 상태에서 전화가 왔을때, 잠금상태, 멀티태스킹 스크린)
        -   **Active** 앱이 실행중이며 현재 이벤트를 받고 있고 발생한 상태
-   **Background** : 앱이 백그라운드에 있는 상태이지만 여전히 실행되고있는 코드가 있는 상태
    -   Foreground 상태에서 HomeScreen으로 이동한 상태
    -   Background 상태로 전환되기 전에 호출된 Task가 끝나지 않은 경우 Background상태에서도 실행됩니다.
    -   Background 상태에서 후출된.  Task는 App이 Foreground 상태로 전환된 후에 실행됩니다.
-   **Suspened** : 앱이 백그라운드에 있고 실행되는 코드가 없는 상태 (App은 여전히 메모리에 존재하며 Suspend 상태가 될 당시의 상태를 저장하고 있지만, CPU나 배터리를 소모하지 않습니다. 언제든지 메모리 부족등의 이유로 종료됨.)
    -   App이 Background 상태로 전환된 후 더이상 작업을 수행하지 않으면 System에서 App을 Suspend 상태로 전환합니다.
    -   App은 여전히 메모리에 존재하며 Suspend 상태가 될 당시의 상태를 저장하고 있지만, CPU나 배터리를 소모하지 않습니다.
    -   Suspend 상태의 App은 Foreground 상태의 App을 위해 메모리 부족 등의 이유로 System에 의해 언제든지 종료됩니다. 이후 App을 실행하면 이전 상태의 화면은 나오지않고 App이 재시작됩니다.



## More

[자세한 설명](https://medium.com/cashwalk/ios-background-mode-9bf921f1c55b)

Backgrounds 상태에서의 자세한 설명을 포함합니다.

