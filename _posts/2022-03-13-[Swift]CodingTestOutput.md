---
title: '출력: 스위프트로 코딩테스트 보기'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트", "코딩 테스트", "Swift"]
---

# 출력
`func print(_ items: Any..., separator: String = " ", terminator: String = "\n")`
items - 여러 파라미터를 넣을 수 있음, separator - 구분자, terminator - end
```Swift
let oneToFive = 1...5
print(oneToFive)
// Prints "1...5"

print(1.0, 2.0, 3.0, 4.0, 5.0, separator: " ... ")
// Prints "1.0 ... 2.0 ... 3.0 ... 4.0 ... 5.0"

for n in 1...5 {
    print(n, terminator: "")
}
// Prints "12345"
```


# More
