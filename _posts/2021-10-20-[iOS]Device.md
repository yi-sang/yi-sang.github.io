---
title: '실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']
---

# 실제 디바이스가 없을 경우, 개발 환경에서 할 수 있는 것과 없는 것



## 할 수 있는 것

-   페이스 iD → 시뮬레이터의 메뉴상에서 인식됨/안됨 처리 가능
-   potrait 가로로 눕히기
-   landscape 세로로 눕히기



## 할 수 없는 것

#### **하드웨어**

------

-   모션인식(가속도 센서, 가압계 센서)
-   근접 센서
-   주변 조도 센서
-   줌인, 줌아웃 등의 기능
-   카메라
-   블루투스
-   마이크
-   전화기능



#### **API**

------

-   Apple의 푸시 알림 수신 및 전송
-   사진,연락처,캘린더에 액세스하기 위해 개인 정보 보호 알림.
-   Handoff 기능
-   UIBackgroundModes Key
-   MessageUI 기능



### Framework

-   외부 액세서리
-   IOSurface
-   Media Player
-   Message UI
-   UIVideoEditorController 클래스
-   Metal, MetalKit 및 Metal Performance Shaders 프레임워크



#### **그 외**

------

-   맥의 성능이 아이폰의 성능보다 훨씬 뛰어나 CPU나 메모리 부담이 얼마나 되는지 알 수 없습니다.
-   네트워크 속도 테스를 할 수 없습니다.
-   페이스 아이디는 직접 얼굴 인식은 안되지만 인식됨,안됨 처리는 해볼 수 있습니다.

