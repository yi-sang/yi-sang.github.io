---
title: 'foreach 반복문'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Foreach 반복문

```swift
import UIKit
// 콜렉션 : 데이터를 모아둔 것
// 배열, 셋, 딕셔너리, 튜플
// 배열

var myArray : [Int] = [0,1,2,3,4,5,6,7,8,9,10]

// 배열의 갯수 만큼 반복합니다.
for item in myArray {
    print("item: \(item)")
}

for item in myArray where item > 5 {
    print("5보다 큰수: \(item)")
}
```

💡콜렉션의 의미에 대해서 배웠고 where을 if대신 쓸 수 있구나!

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

