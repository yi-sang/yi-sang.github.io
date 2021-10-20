---
title: '피신 과정중 Debug 사용법'
categories: ['Practice']
post-image: ../assets/images/42Seoul.jpeg
tags: ["42seoul", "lapicine", "라피신"]
---

**사설**

음,,, 피신 후기를 남기고 싶은데 떨어질 것 같기도 하고 불안해져서 후기는 합격이든 불합격이든 발표가 나오고 나서 작성하려고 한다. 그래서 요즘 c로 백준이라는 사이트에서 c 개념도 재정립할 겸 혹시라도 떨어지게 되면 하게 될 코딩테스트도 준비할 겸 문제를 풀고 있다. 피신이 끝난 다음 날부터 브론즈 5부터 시작하여 현재 브론즈 1이다. 오늘 실버찍고 자야지!!!

vscode도 처음 써보고 깃 add commit push pull 말고도 다른 커맨드도 써보고 이것저것 시간을 많이 쓴다... 누가 알려주는 사람없나... 막막하다... 프론트엔드는 뭐고 백앤드는 뭐고 ㅋㅋㅋㅋ

우선 백준문제 풀어보다가 다음 주부터는 백지상태로 이틀잡고 웹만들어보기 이런것들 해보면서 html css js 맛만 봐보려고한다.

현재는 vscode와 vim에서는 lldb를 사용하여 디버깅하지만 (어제 오늘 익힘 ㅋㅋㅋ) 피신과정중에 디버그사용하려고 고생한 내가 생각나서 글을 남긴다. 지금 사용하는 vscode 디버거와 lldb는 피신 과정중에는 사용이 불가능하다.

(sudo라는 관리자 권한이 없음) 그래서 찾은 방법은 웹사이트를 이용한 디버그.



[https://ide.cs50.io](https://ide.cs50.io/)

[![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fide.cs50.io%2Fstatic%2Fide.png%22&type=ff500_300)](https://ide.cs50.io/)[**CS50 IDE**CS50 IDE integrated development environment for students and teachers Log in or browse documentationide.cs50.io](https://ide.cs50.io/)

우선 회원가입하고 로그인을 하고 들어가면

아래와 같은 창이 뜬다. 

(만약 빈 화면이라면 alt + n 으로 새로운 파일창을 만들어주고 alt + t 로 새로운 터미널을 만들고 터미널을 드래그하여서 아래와 같이 만들어 주자)

![image](https://user-images.githubusercontent.com/80687913/138138699-690417a3-953d-46f0-9d11-352e9202bd88.png)

그리고  ctrl + s 로 파일명을 지정해준다.(.c붙여야됨)

![image](https://user-images.githubusercontent.com/80687913/138138666-97f39700-f8f6-451e-ab43-7d1b90d95e41.png)

간단한 코드를 구성해봤다.

파일에서

**[#include](https://blog.naver.com/PostListByTagName.naver?blogId=westernize&encodedTagName=include) <cs50.h>** 로 헤더를 추가해주고



터미널에서는

**gcc -g** (**파일명.c**) **-o** (**생성할 실행파일명**)  // 디버그 사용하려면 -g 옵션을 줘야한다! 

**debug50 ./**(**생성할 실행파일명**) 을 치면

![image](https://user-images.githubusercontent.com/80687913/138138627-4365dd83-05d8-4589-a18f-11ccdba9a169.png)

몇 초 기다리면 라인에 노란 줄이 생기는 데 

**F10** 다음 단계로 이동

**F9**   다음 프로시저로 이동

를 이용해서 사용하고  터미널 창에서 **ctrl + c** 로 디버그에서 빠져나온다.



느리긴 한데 진짜 편리하고 보면 볼 수록 꿀이다. 컴파일시 문제 발생하면 해경방안을 요구하는 help50 이런 것도 사용할 수 있으니 관심 있는 사람은 [모두를 위한 컴퓨터 과학 (CS50 2019) 강좌소개 : 부스트코스 (boostcourse.org)](https://www.boostcourse.org/cs112) 여기 들어가서 로그인하고 수강신청해서 보길... 피신 준비하면서 정렬이랑 포인터, 동적할당부분은 보면 좋을 것 같다.

다음에는 우분투에서 vscode사용하여 디버그 사용하는 법 lldb사용하는 법등 일기식으로 정리해야겠다.

(합격시켜줘)