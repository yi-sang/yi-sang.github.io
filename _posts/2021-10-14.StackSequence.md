---
title: '스택 수열 - 1874'

post-image: ../assets/images/algorithmStudy.jpg

categories: ['Algorithm']

tags: ['스택']


---

# 스택 수열

# 문제

스택 (stack)은 기본적인 자료구조 중 하나로, 컴퓨터 프로그램을 작성할 때 자주 이용되는 개념이다. 스택은 자료를 넣는 (push) 입구와 자료를 뽑는 (pop) 입구가 같아 제일 나중에 들어간 자료가 제일 먼저 나오는 (LIFO, Last in First out) 특성을 가지고 있다.

1부터 n까지의 수를 스택에 넣었다가 뽑아 늘어놓음으로써, 하나의 수열을 만들 수 있다. 이때, 스택에 push하는 순서는 반드시 오름차순을 지키도록 한다고 하자. 임의의 수열이 주어졌을 때 스택을 이용해 그 수열을 만들 수 있는지 없는지, 있다면 어떤 순서로 push와 pop 연산을 수행해야 하는지를 알아낼 수 있다. 이를 계산하는 프로그램을 작성하라.

## 입력

첫 줄에 n (1 ≤ n ≤ 100,000)이 주어진다. 둘째 줄부터 n개의 줄에는 수열을 이루는 1이상 n이하의 정수가 하나씩 순서대로 주어진다. 물론 같은 정수가 두 번 나오는 일은 없다.

## 출력

입력된 수열을 만들기 위해 필요한 연산을 한 줄에 한 개씩 출력한다. push연산은 +로, pop 연산은 -로 표현하도록 한다. 불가능한 경우 NO를 출력한다.

## 예제 입력 1 복사

```
8
4
3
6
8
7
5
2
1
```

## 예제 출력 1 복사

```
+
+
+
+
-
-
+
+
-
+
+
-
-
-
-
-
```

## 예제 입력 2 복사

```
5
1
2
5
3
4
```

## 예제 출력 2 복사

```
NO
```

## 힌트

1부터 n까지에 수에 대해 차례로 [push, push, push, push, pop, pop, push, push, pop, push, push, pop, pop, pop, pop, pop] 연산을 수행하면 수열 [4, 3, 6, 8, 7, 5, 2, 1]을 얻을 수 있다.

## On my way

```python
import sys
stack = []
answer = []
count = 0

a = int(sys.stdin.readline().rstrip())
for i in range(a):
    b = int(sys.stdin.readline().rstrip())
    while count < b:
        count += 1
        stack.append(count)
        answer.append("+")

    if stack[-1] == b:
        stack.pop()
        answer.append("-")
    else:
        print("NO")
        break
else:
  for i in answer:
     print(i)
```

💡문제를 이해하기가 어려웠다. 아직 스택이 익숙하지 않아서 그런 것 같다.

## On other way

```python
n = int(input())
count = 0
stack = []
result = []
no_message=True

for i in range(0,n):
    x = int(input())

    while count < x:
      count += 1
      stack.append(count)
      result.append("+")

    if stack[-1]==x:
        stack.pop()
        result.append("-")
    else:
        no_message = False
        exit(0) #a clean exit without any errors / problems

if no_message==False:
    print("NO")
else:
    print("\n".join(result))
```

💡`print("\n".join(result))` 고차함수를 이용한 방법 알아두면 좋겠다.

