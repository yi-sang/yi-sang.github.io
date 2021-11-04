---
title: '자신만의 Custom View 만들기'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']


---

# 자신만의 Custom View 만들기

**custom view**는 **스토리보드, Xib**, 그리고 **코드**  로 구성할 수 있다.

| 장단점 | **Xib사용**                                                  | **코드사용**                                                 |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 장점   | 직관성: 눈으로 쉽게 보면서 레이아웃 작업가능 <br />(레이아웃 에러시 레이아웃 찾기쉬움)<br />편의성: 뷰 컨트롤러에 추가적인 코드작업 필요없음<br /> | 어떤 일이 일어나는지 알 수 있음<br />개발자 마음대로 제어가 가능(동적 레이아웃)<br /> 충돌시 해결이 쉬움 |
| 단점   | 충돌시 해결이 어려움<br />코드로 작성한 UI에 비해서 오버헤드가 큼 (필요시 메모리로드->파싱과정..) | 개발기간이 Xib에비해서 오래걸림<br />레이아웃 에러찾기 어려움<br />오래된 코드 리팩토링 어려움 |

1.  `init(coder:)` **스토리보드**

    내가 구성한 view의 상태를 앱의 disk에 저장하는 과정을 `serialize`라고 한다. `deserialize` 는 반대로 disk에 저장된 상태를 불러오는 작업이라고 볼 수 있다. `NSCoding`이라는 프로토콜을 통해 이 serialize와 deserialize 작업이 가능해진다.

    Storyboard라는 interface builder를 사용하여 view의 상태를 수정할 경우 serialization 작업을 Xcode가 `init(coder:)`를 호출하여 앱 내 view 작업을 저장하고 불러오는 작업을 해준다. 

2.  `awakeFromNib()` **Xib**

    cell은 xib로도 많이 작성합니다. xib로 작성을 하게되면 `awakeFromNib`에서 초기화를 시켜주어야 한다. 해당 메서드는 `view.register(nib:, forCellWithReuseIdentifier:)` 시점에서 불리게 된다.

3.  `init(frame:)` **코드**

    `init(frame:)` 을 코드로 작성하면 initialize를 cg rect bounds를 지정해 주는데 frame을 호출해서 초기화를 해줍니다.`view.register(_:, forCellWithReuseIdentifier:)` 시점에서 불리게 된다.

---

여기서 의문이 생길 수 있다.

`init(coder:)`이니셜라이저가 필요한 이유는 스토리보드를 통해 UI를 초기화하기 위해 필요하다.

하지만 storyboard를 사용할 때에는 해당 이니셜라이저를 선언할 필요가 없다.

코드로 UI작성을 할 때는 해당 이니셜라이저를 사용하지 않음에도 불구하고 view를 구현할 때 선언 해주어야 한다.

그 이유는 무엇일까?

이 `init(coder:)`는 NSCoding이라는 프로토콜에 정의되어 있다. 이 프로토콜은 표준 키 기반 아카이브를 통해서 직렬화가능한 클래스에 적용되는데, UI를 구성할 수 있는, 그러니까 nib 파일에 들어갈 수 있는 모든 클래스는 이 프로토콜을 따르고 있다. 그런데 이때 요 이니셜라이저는 convenience가 붙지 않은, 지정 이니셜라이저이다. 

Swift는 기본적으로 서브클래스가 수퍼클래스의 이니셜라이저들을 상속받지 않은 것을 원칙으로 하고 특별한 경우에 자동 상속을 허용한다. 이니셜라이저의 자동상속은 다음의 조건을 만족해야 한다.

1.   만약 자식 클래스에서 추가된 저장 프로퍼티가 모두 디폴트 값을 가지고 있고, 추가적인 지정 이니셜라이저를 작성하지 않았다면(여기서는 추가되는 지정이니셜라이저 혹은 지정이니셜라이저의 오버라이드가 모두 포함된다.) 부모 클래스의 모든 지정 이니셜라이저를 상속받는다.
2.   부모의 이니셜라이저를 상속받았거나, 아니면 부모의 모든 지정 이니셜라이저를 오버라이드했다면 부모의 편의 이니셜라이저를 자동으로 상속받는다.


init(frame:)을 오버라이드했다는 것은 부모의 일부 지정 이니셜라이저를 오버라이드했다는 것이다. 이 경우에는 이니셜라이저 상속을 포기한 것이 되고, init(coder:) 는 자동으로 상속되지 않기 때문에 수동으로 직접 작성해야 한다.

\- init() 단계 frame or Layer 관련 없는 값들 설정

\- awakeFromNib 단계에는 frame 이나 Layer 관련된 값들을 설정하고 구현

\- autoLayout 설정은 awakeFromNib 이후

프로토콜에 명시된 이니셜라이저를 구현하면 required 키워드가 붙여주어야합니다.



## required

프로토콜에 명시된 이니셜라이저를 구현하면 required 키워드가 붙여주어야합니다.UIView와 UIViewController는 NSCoding 프로토콜을 구현하고 있으므로, `init?(coder:)`를 구현해줘야 하고 앞에 꼭 required를 붙여줘야합니다.

해당 프로토콜을 준수하는 **클래스**에서 프로토콜에서 요구하는 이니셜라이저 요구사항을 구현할 수 있습니다.

designated init 또는 convenience init으로말이죠.

두 경우 모두 "required"라는 modifier를 표시해야합니다.









## MORE

[자세한 설명](https://velog.io/@inwoodev/iOS-initframe-initcoder)

[designated init vs convenience init](https://ios-development.tistory.com/542)

[required](https://zeddios.tistory.com/256)
