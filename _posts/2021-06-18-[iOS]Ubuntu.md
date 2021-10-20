---
title: 'Ubuntu에 Swift 최신 버전 설치'
categories: ['iOS']
post-image: ../assets/images/Apple-iOS.png
tags: ["스위프트", "ubuntu"]
---

# Ubuntu에 Swift 최신 버전 설치

애플의 스위프트는 오픈소스로 리눅스 사용자와 윈도우 사용자(ubuntu)도 사용할 수 있다.

 

우선 우분투가 깔려있어야 한다.



2021년 06월 기준

우분투 최신 버전 : 20.04

스위프트 최신 버전 : 5.4.1



[우분투(Ubuntu)에 스위프트 설치하기 - yagom's blog](https://blog.yagom.net/535/)



글의 대부분을 야곰님의 블로그를 참조하면

서 헤맸던 부분을 보완했습니다.



**스위프트 설치**



우선 sudo 권한을 주고,

DESKTOP-D8D0DAM% su Password:

의존성 관리도구를 통해 필요한 패키지(clang, libicu-dev)를 먼저 설치.

apt-get install clang libicu-dev

스위프트 소스를 다운로드 해야하는 데 우분투 자체에서 스위프트 패키지를 다운로드 하기 위해 wget을 설치한다.

apt-get install wget

스위프트 패키지를 다운로드 할 건데 홈에 설치하고 이동하여 준다.

(혹시 현재 폴더에 설치하고 싶다면 ~/swift_package 를 ./swift_package 로 바꿔주면 된다.)

mkdir ~/swift_package cd ~/swift_package

[Swift.org - Download Swift](https://swift.org/download/#releases) 들어가서 본인 버전에 마우스를 대고 오른쪽 마우스를 눌러 링크복사를 클릭한다.

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMjk5/MDAxNjIzOTYxNTE1ODUw.YuxXby-9EEta9JhAUarX1O-HtINT8D_oXBZIz1toBAYg.amruMHXb4egEuf85S6dNFpAVr3vw9o6ik9297hNjMgkg.PNG.westernize/image.png?type=w773)

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMzAw/MDAxNjIzOTYxNTc3MTc2.xf-ExTbegeVdGVt1y-ludFnQLkGo1Txk-tOJk2o5GW4g.naubmRgEY1m6lsOhs61NWk4R5-0k5rl-sZpQWShgA_0g.PNG.westernize/image.png?type=w773)

wget을 이용해서 다운로드한다. (wget 뒤에 복사한 링크 ctrl + v)

wget ﻿https://swift.org/builds/swift-5.4.1-release/ubuntu2004/swift-5.4.1-RELEASE/swift-5.4.1-RELEASE-ubuntu20.04.tar.gz

처음으로 Swift를 설치한다면 다운로드 후에 GPG 키를 추가해주어야 한다.

wget -q -O - https://swift.org/keys/all-keys.asc | gpg --import -

다운로드한 스위프트 패키지의 압축을 풀어준다.

tar xzf swift-5.4.1-RELEASE-ubuntu20.04.tar.gz

압축을 해제하고 /opt 폴더로 이동한다. 폴더명도 swift-5.4.1로 수정한다.

mv swift-5.4.1-RELEASE-ubuntu20.04 /opt/swift-5.4.1

cd(chang directory) 명령어를 이용하여 /opt 폴더로 이동하고

ls(list) 명령어를 통해 swift-5.4.1 폴더가 있는지 확인한다.

cd /opt ls

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMjA4/MDAxNjIzOTYyMjE5Mjkw.kONSXzhcn7TUr-ZReFtPd2IW8M-rUAu0Ho-r2al_srIg.qvTwRp70BunHw0pb1QNxW19NPigBeq_ejunYaptqOwog.PNG.westernize/image.png?type=w773)

vim 을 이용해 .bashrc를 열어주고 파일 맨 밑에 환경 변수를 등록해준다. (기본)

vim ~/.bashrc

export PATH=/opt/swift-5.4.1/usr/bin:"${PATH}"

zsh가 기본 쉘이라면 (oh-my-zsh) .zshrc파일을 열고 맨 밑에

export PATH=/opt/swift-5.4.1/usr/bin:"${PATH}"를 붙여넣기한다.

vim ~/.zshrc

export PATH=/opt/swift-5.4.1/usr/bin:"${PATH}"

:wq로 저장한다.

:wq

.bashrc파일 혹은 .zshrc 파일을 적용한다.

source ~/.bashrc﻿ source ~/.zshrc

올바르게 설치되었는지 버전을 확인한다.

swift --version

![img](https://postfiles.pstatic.net/MjAyMTA2MThfNzMg/MDAxNjIzOTYzMTA1Nzc4.kc72dsXV15Nu5s7H5aSfJSac7ALTubT9P92mGv0BgQcg.ET_dt1yuXWz2sm-9CvhKcZOfhFQEyG4Q7Uj_1PfJpMsg.PNG.westernize/image.png?type=w773)

파이썬을 설치해준다.

apt-get install libpython-dev

**스위프트 작성 및 실행**

****

드디어 swift 콘솔창에 들어갈 수 있다, hello world도 해보고, 간단한 연산도 해보고 :q를 통해 나올 수 있다.

swift print("hello world!!") 1 + 1 :q

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMTM1/MDAxNjIzOTYzNTAxNzUz.Z2MbDg2OFb7YXxX_8BJq_Et3UMY4FZLLGeU81JS61z4g.HaK-MoCoF6dj6gxtqE6AXbLatM6HZ3tbl0iReQrx7AUg.PNG.westernize/image.png?type=w773)

스위프트 파일을 vim을 이용해서 만들어주고 실행한다.

vim test.swift

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMTYz/MDAxNjIzOTYzOTMwNjQ2.Hj9s_SGGX03jp-T6mMSPkXOdw9oFpgaYC9fLb8WPUcsg.Alajv0-l3IoN6SYhVPQP58qUgZfUVHS516IRBxWOYNAg.PNG.westernize/image.png?type=w773)

swift test.swift

![img](https://postfiles.pstatic.net/MjAyMTA2MThfMTEg/MDAxNjIzOTYzOTY5NzY2.OvJH6gD1deLviWMfx0f1UjFzFnHw7iV2hKfjPDG67Cog.CyDxNxf6oGmNuwpK9CFmVfgxLJ1uDgMIRkeOBZ0YHAsg.PNG.westernize/image.png?type=w773)



스위프트 강의는 boostcourse에서 무료로 들을 수 있다.



[iOS 프로그래밍을 위한 스위프트 기초 강좌소개 : 부스트코스 (boostcourse.org)](https://www.boostcourse.org/mo122)