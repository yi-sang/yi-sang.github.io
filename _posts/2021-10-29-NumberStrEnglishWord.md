---
title: '숫자 문자열과 영단어'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['2021 카카오 채용연계형 인턴십']
---

# 숫자 문자열과 영단어

###### 문제 설명

![img1.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/d31cb063-4025-4412-8cbc-6ac6909cf93e/img1.png)

네오와 프로도가 숫자놀이를 하고 있습니다. 네오가 프로도에게 숫자를 건넬 때 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다.

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.

-   1478 → "one4seveneight"
-   234567 → "23four5six7"
-   10203 → "1zerotwozero3"

이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 `s`가 매개변수로 주어집니다. `s`가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.

참고로 각 숫자에 대응되는 영단어는 다음 표와 같습니다.

| 숫자 | 영단어 |
| ---- | ------ |
| 0    | zero   |
| 1    | one    |
| 2    | two    |
| 3    | three  |
| 4    | four   |
| 5    | five   |
| 6    | six    |
| 7    | seven  |
| 8    | eight  |
| 9    | nine   |

------

##### 제한사항

-   1 ≤ `s`의 길이 ≤ 50
-   `s`가 "zero" 또는 "0"으로 시작하는 경우는 주어지지 않습니다.
-   return 값이 1 이상 2,000,000,000 이하의 정수가 되는 올바른 입력만 `s`로 주어집니다.

------

##### 입출력 예

| s                    | result |
| -------------------- | ------ |
| `"one4seveneight"`   | 1478   |
| `"23four5six7"`      | 234567 |
| `"2three45sixseven"` | 234567 |
| `"123"`              | 123    |

------

##### 입출력 예 설명

**입출력 예 #1**

-   문제 예시와 같습니다.

**입출력 예 #2**

-   문제 예시와 같습니다.

**입출력 예 #3**

-   "three"는 3, "six"는 6, "seven"은 7에 대응되기 때문에 정답은 입출력 예 #2와 같은 234567이 됩니다.
-   입출력 예 #2와 #3과 같이 같은 정답을 가리키는 문자열이 여러 가지가 나올 수 있습니다.

**입출력 예 #4**

-   `s`에는 영단어로 바뀐 부분이 없습니다.

------

##### 제한시간 안내

-   정확성 테스트 : 10초

## On my way

```python
def solution(s):
    answer = ""
    dic = {"zero":'0', "one":'1', "two":"2", "three":"3", "four":"4",\
           "five":"5", "six":"6", "seven":"7", "eight":"8", "nine":"9"}
    temp = 0
    
    for i, v in enumerate(s):
        if v.isdigit():
            answer += v
        else:
            if s[i:i+3] in dic:
                answer += dic[s[i:i+3]]
                i += 3
            elif s[i:i+4] in dic:
                answer += dic[s[i:i+4]]
                i += 4
            elif s[i:i+5] in dic:
                answer += dic[s[i:i+5]]
                i += 5
    return int(answer)
```

💡

`dic = {"zero":'0', "one":'1', "two":"2", "three":"3", "four":"4",\
           "five":"5", "six":"6", "seven":"7", "eight":"8", "nine":"9"}`

`\`를 붙여서 가독성 좋게 쓸 수 있다.

`if s[i:i+3] in dic:`  이런 조건을 붙이기가 어렵다.

`answer += dic[s[i:i+3]]` 딕셔너리에 접근하는 방법 익숙하지 않다.

`return int(answer)` 프로그래머스에서는 "123"과 123은 다르다.

## More

[참고](https://otugi.tistory.com/101)