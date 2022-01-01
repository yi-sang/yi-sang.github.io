---
title: 'enum 자료 구조'
categories: ['Swift']
post-image: ../assets/images/Swift-Logo.png
tags: ["스위프트 기초 문법"]
---

# Enum 자료구조

```swift
import UIKit

enum Grade : Int {
    case first = 1
    case second
}

let yourGrade = Grade.second.rawValue
print("yourGrade: \(yourGrade)")
// yourGrade: 2
enum SchoolDetail {
    case elementary(name: String)
    case middle(name: String)
    case high(name: String)
    
    func getName() -> String {
        switch self {
        // 파라미터를 사용하기 위한 방법
        case .elementary(let name):
            return name
        case let .middle(name):
            return name
        case .high(let name):
            return name
        }
    }
}

let yourMiddleSchoolName = SchoolDetail.middle(name: "부평서중학교")

print("yourMiddleSchoolName: \(yourMiddleSchoolName.getName())")
// yourMiddleSchoolName: 부평서중학교
```

💡첫 번째 rawValue에 정수를 할당하면 1씩 증가한다.

`case let .caseName(term)`

`case .caseName(let term)`

을 사용해도 된다.

# More

[개발하는 정대리](https://www.youtube.com/c/개발하는정대리/playlists])

