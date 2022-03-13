---
title: '문서 검색 - 1543'
post-image: ../assets/images/algorithmStudy.jpg
categories: ['Algorithm']
tags: ['탐색']
---
# 문서 검색 

# 문제
세준이는 영어로만 이루어진 어떤 문서를 검색하는 함수를 만들려고 한다. 이 함수는 어떤 단어가 총 몇 번 등장하는지 세려고 한다. 그러나, 세준이의 함수는 중복되어 세는 것은 빼고 세야 한다. 예를 들어, 문서가 abababa이고, 그리고 찾으려는 단어가 ababa라면, 세준이의 이 함수는 이 단어를 0번부터 찾을 수 있고, 2번부터도 찾을 수 있다. 그러나 동시에 셀 수는 없다.

세준이는 문서와 검색하려는 단어가 주어졌을 때, 그 단어가 최대 몇 번 중복되지 않게 등장하는지 구하는 프로그램을 작성하시오.

## 입력
첫째 줄에 문서가 주어진다. 문서의 길이는 최대 2500이다. 둘째 줄에 검색하고 싶은 단어가 주어진다. 이 길이는 최대 50이다. 문서와 단어는 알파벳 소문자와 공백으로 이루어져 있다.

## 출력
첫째 줄에 중복되지 않게 최대 몇 번 등장하는지 출력한다.

## 예제 입력 1
ababababa
aba
## 예제 출력 1
2
## 예제 입력 2
a a a a a
a a
## 예제 출력 2
2
## 예제 입력 3
ababababa
ababa
## 예제 출력 3
1
## 예제 입력 4
aaaaaaa
aa
## 예제 출력 4
3

## On my way

```python
firstData = input().rstrip()
secondData = input().rstrip()
i, j, cnt = 0, 0, 0
firstLen = len(firstData)
secondLen = len(secondData)
tempLen = secondLen
while True:
    if i >= firstLen+1:
        break
    if firstData[i:tempLen] == secondData:
        i += secondLen
        tempLen += secondLen
        cnt += 1
    else:
        i += 1
        tempLen += 1
print(cnt)      
```
💡 for-in 으로 풀 때는 index가 하나씩만 오르는 상황일 때 적합하다
index를 건드리는 경우에는 while이 적합하다.