---
title: '구글 서치 콘솔 사이트맵 가져올 수 없음'
post-image: ../assets/images/Blog.jpg
categories: ['Blog']
tags: ['사이트맵', 'sitemap']
---

# 구글 서치 콘솔 사이트맵 가져올 수 없음

![image](https://user-images.githubusercontent.com/80687913/139812796-c6b2203e-6695-4575-b3af-38ea32719124.png)

(사실 처음에는 아예 일반 HTTP 오류라는 문구도 안떴다.)

블로그를 개설하면서 여러 어려운 점이 있었지만 이번이 진짜 막막했던것같다.

사이트맵을 정상적으로 만들고 구글 서치 콘솔에 올렸음에도 불구하고 자꾸 가져올 수 없음이라는 문구가 떴기 때문이다.

구글링을 해보면 

1.  sitemap.xml을 입력하지 말고 /sitemap.xml로 입력해보기.

2.  Sitemap.xml로 입력해보기

3.  sitemap내부의 

    `<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLoca    tion="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/sc    hemas/sitemap/0.9/sitemap.xsd" xmlns="http://www.sitemaps.org/schemas/sitema    p/0.9"> `

    대신에 

    `<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">` 로 바꿔보기  

    

4.  feed를 제출하기 rss를 제출하기

5.  삭제했다가 다시 해보기

    

    등 여러가지 방법들이 많은 데



## **내가 해결한 방법** (불 필요한 동작이 있을 수 있음)

1.   **우선 sitemap부터 다시 만들자.. (확실하게 만들어져있다면 아래 2번으로 가자)** 

     _config.xml가 있는 루트 폴더에 있는 sitemap, feed를 삭제하기.

     Gemfile.lock도 삭제하자

     Gemfile에 들어가서 

     <img width="341" alt="image" src="https://user-images.githubusercontent.com/80687913/139818592-27983965-7260-4891-9942-096831dc1ae1.png"> 

     ` gem "jekyll-sitemap"
     gem "jekyll-feed"`

     를 입력해주고 나와서

     

     `bundle install` 을 실행해준다.

     

     _config.yml 파일에 들어가서

     <img width="232" alt="스크린샷 2021-11-02 오후 6 05 47" src="https://user-images.githubusercontent.com/80687913/139817490-ff2eaf10-2aa0-43a6-90d5-dfd021c6de10.png">

     \- jekyll-sitemap

     \- jekyll-feed

     를 입력해주고 나온다.

     

     git add .

     git commit -m "Add: sitemap"

     git push

     로 보내면 된다.



​		확인해보고 싶다면 _site/ 에 들어가면 생성되어 있다.



2.   **본격적으로 사이트맵을 적용해보자.** 

![스크린샷 2021-11-02 오후 5 48 08](https://user-images.githubusercontent.com/80687913/139814585-8ecde980-6569-4e40-89b0-c7d5370771d1.png)

제일 먼저 할 일은 여기에 구글 서치 콘솔 제일 위에 

https://깃헙아이디.github.io을 넣는 것이다.

![image](https://user-images.githubusercontent.com/80687913/139815318-508f94a9-9623-41eb-9b6c-f44736719b03.png)

그 다음으로 색인 생성 요청, 실제 URL테스트를 진행하는 것이다.

그리고 

https://깃헙아이디.github.io/sitemap.xml

https://깃헙아이디.github.io/feed.xml 도 차례로 진행하자.

그리고 

<img width="931" alt="image" src="https://user-images.githubusercontent.com/80687913/139819212-b9cca3a0-540b-42c1-aa68-d7de44fedfb9.png">

새 사이트맵 추가에 혹시 모르니까

sitemap, sitemap.xml

feed, feed.xml을 넣어주자.

가져올 수 없음 이 뜰 텐데 반복하지 말고

다음 날이면 아래처럼 성공으로 바뀔 것이다.

이게 사이트맵을 추가한다고 계속 검색을 하는 게 아니라 **위에서 색인 생성이 완료 되어야 한다.** (이걸 몰라서 뻘 짓을 며칠 함...)

근데 이상한 점은 왜 하나는 sitemap이 성공했고 하나는 feed.xml이 성공했냐는 건데 이건 잘모르겠다. 

나도 오늘 성공한거라... 좀 더 봐야할 것 같다. 아마도 나중에 sitemap.xml과 feed도 성공으로 바뀌지 않을까.. 제출한 시간에 따라서 달라질 수도 있는 거고..

![스크린샷 2021-11-02 오후 5 36 56](https://user-images.githubusercontent.com/80687913/139812818-48c34e7b-93fa-4355-869e-a650bd174b5f.png)

내가 고생한 흔적들...

설명을 잘 못했지만 누군가에게는 도움이 됐으면 좋겠다.

