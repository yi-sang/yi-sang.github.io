---
title: '잃어버린 괄호- 1541'

post-image: ../assets/images/algorithmStudy.jpg

categories: ['Algorithm']

tags: ['그리디']

---

# 잃어버린 괄호

# 문제

세준이는 양수와 +, -, 그리고 괄호를 가지고 식을 만들었다. 그리고 나서 세준이는 괄호를 모두 지웠다.

그리고 나서 세준이는 괄호를 적절히 쳐서 이 식의 값을 최소로 만들려고 한다.

괄호를 적절히 쳐서 이 식의 값을 최소로 만드는 프로그램을 작성하시오.

## 입력

첫째 줄에 식이 주어진다. 식은 ‘0’~‘9’, ‘+’, 그리고 ‘-’만으로 이루어져 있고, 가장 처음과 마지막 문자는 숫자이다. 그리고 연속해서 두 개 이상의 연산자가 나타나지 않고, 5자리보다 많이 연속되는 숫자는 없다. 수는 0으로 시작할 수 있다. 입력으로 주어지는 식의 길이는 50보다 작거나 같다.

## 출력

첫째 줄에 정답을 출력한다.

## 예제 입력 1

```
55-50+40
```

## 예제 출력 1

```
-35
```

## On my way

```python
expression = input().split("-")
ans = 0
for i in expression[0].split("+"):
    ans += int(i)

for i in expression[1:]:
    for j in i.split("+"):
        ans -= int(j)

print(ans)
```

💡 eval() 함수를 쓰면 000123같은 숫자는 계산할 수 없다.

## On other way

```python
import sys
word = sys.stdin.readline().rstrip()
int_word = ''
tmp = ''
minus = False
for w in word:
    if w == '-':
        minus = True
        if tmp !='':
            int_word += str(int(tmp)) + w
        if int_word =='':
            int_word = w
        tmp = ''
    elif w == '+':
        if minus:
            w = '-'
        if tmp !='':
            int_word += str(int(tmp)) + w
        tmp = ''
    else :
        tmp += w
if tmp != '':
    int_word += str(int(tmp))
print(eval(int_word))
```

💡str(int(tmp)) 이런식으로 해결할 수 있다.