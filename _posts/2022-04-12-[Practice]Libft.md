---
title: 'Project - Libft'
categories: ['Practice']
post-image: ../assets/images/42Seoul.jpeg
tags: ["42seoul", "Cadet", "Project", "Libft"]
---
# 첫 과제
클러스터는 매일 오려고 하고 있지만 과제를 하기로 마음 먹기까지는 꽤 오래 걸렸다.포트폴리안을 끝내고 하자는 마음 +  콘파머가 2주간 쉬기로 했기 때문에 지금이 좋은 타이밍이라고 생각한 것이다.

C와 꽤 가까워 졌다고 생각했지만 다시 만나보니 쉽지 않았다. 알고리즘이 어려운 거라기 보다는 어떤 예외가 있을 지 생각하는 것과 이런 것도 처리를 해줘야하나? 라는 고민이 컸다. man을 찾아보는 것을 목표로 노력했으나 결국은 여러 선배 블로그를 참고하였다.

# Libft?
Libft는 자신이 사용할 라이브러리를 만드는 과제이다.

42에서 header의 사용에는 제약이 많기 때문에

내가 후에 있을 과제에서 사용할 라이브러리를 만들어두는 것이다.

메모리 누수 처리해야하고, norm을 준수해야하며, Makefile 사용해서 만들어야한다.

## *void
C언어에서는 형태가 다른 포인터끼리의 초기화는 금지되어있다.
하지만 void 포인터를 사용하면 어떤 포인터든 저장할 수 있다.
역 참조가 안 되기 때문에 함수의 인자값으로 사용하고 강제형변환을 통해 사용한다.

## 강제형변환
강제형변환을 사용한다고 했는데 어떤 형으로 변환할까?

`unsigned char *`이다.
### 왜 unsigned char *을 사용할 까?
메모리를 1바이트씩 접근하기 위해서이다.

### char *도 있는데...?
포인터는 주솟값 연산이니까 부호를 쓰지 않는다.
그러므로 부호 비트를 사용하지 않아서 1바이트(8비트) (2^8) (0~255)를 온전히 사용할 수 있다는 점이다.

ps. C 언어 표준에서는 char의 부호가 정해져 있지 않다.
하지만 C언어는 오래된 언어이기 때문에 관례가 있다.
동시에 제약이 없는 언어이니까 하면 안 되는 것들을 하는 것도 허용이 된다. 비교적 최근에 나온 언어들은 설계 단계부터 하지 말아야 할 것은 철저하게 금지하는 방향으로 개발되었다.

-> 함수의 인자로 void*를 받고 메모리에 접근하기 위해서는 unsigned int *를 사용하여 안전하게 메모리 주소값을 처리하자.

```c
void ft_bzero(void *s, size_t n)
{
    unsigned char   *start_ptr;
    
    start_ptr = (unsigned char *)s;
    .
    .
    .
}
```
## const char *p VS char *const p
우선 const는 불변을 의미한다. 상수!
### const char *p
const (char *)p
포인터 p의 자료형은 const char이다.
포인터 p의 자료형은 상수 char이다.
포인터 p는 char인 데 값을 바꿀 수 없다.

포인터지만 안에 값을 바꿀 자격은 없다.
```c
int main(void)
{
    char str[20] = "Swift";
    const char *char_ptr = str;

    *(char_ptr + 1) = 'C' //에러
    *char_ptr++; // 포인터이므로 당연히 가능하다.
}
```

### char *const p
(char *)const p
상수 p는 char 형을 가르킨다.
상수 p는 char 형 포인터이다.
char 형을 가리키는 주소값이 상수이다.

한 주소값만 바라보는 해바라기
```c
int main(void)
{
    char str[20] = "Swift";
    const char *char_ptr = str;

    *(char_ptr + 1) = 'C' // 가능하다. 
    *char_ptr++; // 해바라기므로 에러
}
```

### const char *const p
값도 못바꾸고 주소값도 못 바꾼다.

## size_t 자료형
문자열이나 메모리 사이즈를 나타낼 때 사용하는데

(C99 표준)
'이론상 가장 큰 사이즈를 담을 수 있는 unsigned 데이터 타입'으로 정의 되어 있다.

운영체제가 32비트냐 64비트냐에 따라
size_t는 부호가 없는 32비트 자료형 정수, 부호가 없는 64비트 자료형 정수로 정의 된다.

unsigned int는 4,294,967,295까지 표현한다.
(바람의 나라 최대 경험치는 42.9억이다.)

향후 등장할지도 모르는 128비트 머신이라던가 더 큰 머신이 존재한다면 그에 따라 더 큰 사이즈가 될 것이다.

## 함수 포인터
함수의 주소를 담은 포인터 변수(4바이트)

## 정적 할당, 동적 할당
### 정적 할당
메모리 할당 방법 중에 하나로, 프로그램 실행의 시작부분에서 필요한 만큼 미리 기억공간을 할당 받고 시작하는 것을 의미한다.

- 장점: 메모리 누수와 같은 문제를 신경쓰지 않아도 된다. 정적 할당된 메모리는 실행 도중에 해제되지 않고, 프로그램이 종료할 때 알아서 운영 체제가 회수한다.
- 단점: 메모리의 크기가 하드 코딩되어 있어서 나중에 조절 할 수 없다. 스택에 할당된 메모리이므로 동적 할당에 비해 할당 받을 수 있는 최대 메모리에 제약을 받는다.

### 동적할당
실행 시간 동안 사용할 메모리 공간을 할당하는 것을 말한다. 사용이 끝나면 운영체제가 쓸 수 있도록 반납하고 다음에 요구가 오면 재 할당을 받을 수 있다. 

동적 할당은 프로세스의 힙영역에서 할당하므로 프로세스가 종료되면 운영 체제에 메모리 리소스가 반납되므로 해제된다.

그러나 프로세스가 계속 실행될 때에는 동적할당 된 영역은 유지되므로 프로그램이 정해진 힙 영역의 크기를 넘는 메모리 할당을 요구하면 할당되지 않는다. 따라서 사용이 완료된 영역은 반납하는 것이 유리한데, 프로그래머가 함수를 사용해서 해제해야 한다.(free)

- 장점: 상황에 따라 원하는 크기만큼의 메모리가 할당되므로 경제적이며, 이미 할당된 메모리라도 언제든지 크기를 조절할 수 있다.

- 단점: 더 이상 사용하지 않을 때 명시적으로 메모리를 해제해 주어야 한다.

할당 - malloc
해제 - free

## null가드
```c
tmp = (char *)malloc(sizeof(char) * size)
if (!tmp)
    return (0);
```
libft에서 malloc을 사용하는 함수들에 널가드를 해줘야할까?

두 경우 모두 과제의 점수에 있어서 영향을 주지는 않는다. 

하지만 추후 구현해놓은 함수를 사용하면서 segment fault가 떠서 어디가 잘못됐는지 확인할 수 있는 것이 좋다면 널가드를 해주지 않아도 되고 segment fault가 안 뜨는게 안정성에 좋다고 생각하면 해줘도 된다.

## 사담
금방 할 줄 알았던 libft 결국 3일동안 몰두했다. 모든 함수를 완벽하게 구현했다고 생각하지 않는다. 하지만 구현하면서 배웠던 지식 특히 노드를 구현하면서 좀 더 발전할 수 있었기에 뿌듯했던 시간이었다.
7월 27일까지 수명이 늘어났다. 남은 기간 CS공부도 꾸준히하고 코테 준비도 꾸준히하고 프로젝트도 잘 마무리하고 싶다.
너무 조급하지 말자. 다만 매 순간 최선을 다하자.