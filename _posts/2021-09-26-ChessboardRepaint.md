---
title: '체스판 다시 칠하기 - 1018'

post-image: ../assets/images/algorithmStudy.jpg

categories: ['Algorithm']

tags: ['브루트 포스']


---

# 체스판 다시 칠하기

## 문제

지민이는 자신의 저택에서 MN개의 단위 정사각형으로 나누어져 있는 M*N 크기의 보드를 찾았다. 어떤 정사각형은 검은색으로 칠해져 있고, 나머지는 흰색으로 칠해져 있다. 지민이는 이 보드를 잘라서 8*8 크기의 체스판으로 만들려고 한다.

체스판은 검은색과 흰색이 번갈아서 칠해져 있어야 한다. 구체적으로, 각 칸이 검은색과 흰색 중 하나로 색칠되어 있고, 변을 공유하는 두 개의 사각형은 다른 색으로 칠해져 있어야 한다. 따라서 이 정의를 따르면 체스판을 색칠하는 경우는 두 가지뿐이다. 하나는 맨 왼쪽 위 칸이 흰색인 경우, 하나는 검은색인 경우이다.

보드가 체스판처럼 칠해져 있다는 보장이 없어서, 지민이는 8*8 크기의 체스판으로 잘라낸 후에 몇 개의 정사각형을 다시 칠해야겠다고 생각했다. 당연히 8*8 크기는 아무데서나 골라도 된다. 지민이가 다시 칠해야 하는 정사각형의 최소 개수를 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 N과 M이 주어진다. N과 M은 8보다 크거나 같고, 50보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에는 보드의 각 행의 상태가 주어진다. B는 검은색이며, W는 흰색이다.

## 출력

첫째 줄에 지민이가 다시 칠해야 하는 정사각형 개수의 최솟값을 출력한다.



## On my way

```python
N, M = map(int, input().split())
original = []
count = []

for _ in range(N):
    original.append(input())

for a in range(N-7):
    for b in range(M-7):
        index1 = 0
        index2 = 0
        for i in range(a, a+8):
            for j in range(b, b+8):
              	# (0, 0)(0, 2)(0, 4)(0, 6)...
                if (i+j) % 2 == 0:
                    if original[i][j] != 'W':
                        index1 += 1
                    elif original[i][j] != 'B':
                        index2 += 1
                # (0, 1)(0, 3)(0, 5)(0, 7)...
                else:
                    if original[i][j] != 'B':
                        index1 += 1
                    elif original[i][j] != 'W':
                        index2 += 1
        # 흑돌과 백돌중 조금 바꿔도 되는 돌을 계산하여 넣어준다.
        count.append(min(index1, index2))

print(min(count))
```

![참고 이미지](https://user-images.githubusercontent.com/80687913/134811538-a2e92869-b74a-47af-a960-ac998a6963d4.png)



8 X 8 형태의 체스판의 모습의 두 가지 형태

흰색부터 시작			검정색부터 시작

WBWBWBWB	|	BWBWBWBW
BWBWBWBW	|	WBWBWBWB
WBWBWBWB	|	BWBWBWBW
BWBWBWBW	|	WBWBWBWB
WBWBWBWB	|	BWBWBWBW
BWBWBWBW	|	WBWBWBWB
WBWBWBWB	|	BWBWBWBW
BWBWBWBW	|	WBWBWBWB

8X8 크기의 체스판을 완전탐색한다.

![시작](https://user-images.githubusercontent.com/80687913/134811316-9b91aa3b-3b34-4a1e-9f74-4d280f953f78.png)

첫 번째 줄부터 탐색하고

![첫번째 줄 끝](https://user-images.githubusercontent.com/80687913/134811325-11e787d7-519f-41f7-9368-75c27f504d53.png)

두 번째 줄또한 탐색한다.

![두번째 줄 시작](https://user-images.githubusercontent.com/80687913/134811331-b81b0e5a-5241-41a9-a986-e6a9673539c4.png)

가로축 끝, 세로축 끝까지 탐색을 마친다.

![맨 끝](https://user-images.githubusercontent.com/80687913/134811335-2c070fcf-cac2-43ff-8a5d-57b6d1c39851.png)

## On other way

```python
import sys
input = sys.stdin.readline
N,M = map(int,input().rstrip().split())

comp = [['W' if (i+j)%2==0 else 'B' for i in range(N)] for j in range(M)]
field = [list(input().rstrip()) for _ in range(N)]
answer = 2501 # 50 * 50
for b_i in range(N-7):
    for b_j in range(M-7):
        cnt = [0,0]
        for h in range(b_i,b_i+8):
            for w in range(b_j,b_j+8):
                if comp[h-b_i][w-b_j]!=field[h][w]:cnt[0]+=1
                else:cnt[1]+=1
        minNum = min(cnt[0],cnt[1])
        if answer > minNum:answer=minNum
print(answer)


# 출처: https://imksh.com/43 [강승현입니다]
```

💡`comp = [['W' if (i+j)%2==0 else 'B' for i in range(N)] for j in range(M)]`

💡`if comp[h-b_i][w-b_j]!=field[h][w]:cnt[0]+=1`

코드는 짧아지지만 지금으로서는 이해하긴 힘든 것 같다.

