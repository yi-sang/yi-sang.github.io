---
title: 'Bounds와 Frame의 차이점'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']
---

# Bounds와 Frame의 차이점

## frame

The frame rectangle, which describes the view’s location and size in its superview’s coordinate system.

**Superview의 좌표시스템 안에서 View의 위치와 크기를 나타냅니다.(상대적)**

Superview : 한 단계 상위뷰

#### 사용예

-   UIView위치나 크기를 설정하는 경우. 

### Declaration

```swift
var frame: CGRect { get set }
```



---



## bounds

The bounds rectangle, which describes the view’s location and size in its own coordinate system.

**View의 위치와 크기를 자신만의 좌표시스템안에서 나타냅니다.** 

## 사용예

-   View내부에 그림을 그릴때 (drawRect).

-   transfomation 후, View의 크기를 알고싶을 때.

-   하위View를 정렬하는 것과 같이 내부적으로 변경하는 경우.

### Declaration

```swift
var bounds: CGRect { get set }
```



## More

**사실상 이게 핵심!**

[자세한 설명 1](https://zeddios.tistory.com/203)

[자세한 설명 2](https://zeddios.tistory.com/231)
