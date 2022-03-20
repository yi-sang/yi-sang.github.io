---
title: 'NSOperationQueue와 GCD Queue'
post-image: ../assets/images/Apple-iOS.png
categories: ['iOS']
tags: ['iOS개발자 되기', '하루 두 개!']

---

# NSOperationQueue와 GCD Queue의 차이점 및

# GCD API 동작 방식과 필요성

## OS 환경에서의 동시성 프로그래밍 지원 종류

-   GCD (Grand Central Dispatch) : 멀티 코어와 멀티 프로세싱 환경에서 최적화된 프로그래밍을 할 수 있도록 애플이 개발한 기술이다.

-   Operation Queue : 비동기적으로 실행되어야 하는 작업을 객체 지향적인 방법으로 사용한다.

## Grand Central Dispatch

 **C언어 기반의 저수준 API**

기본적으로 스레드 풀의 관리를 프로그래머가 아닌 운영체제에서 관리하기 때문에 프로그래머가 작업을 비동기적으로 **간편하게**사용할 수 있다. 프로그래머가 작업을 생성하고 Dispatch Queue에 추가하면 GCD는 작업에 맞는 스레드를 자동으로 생성해서 실행하고 작업이 종료되면 스레드를 제거한다.

## Operation Queue

**Objective-C언어 기반의 고수준 API**

-   Operation의 실행을 관리하며, Operation을 담는 대기열(Queue)이다.
-   대기열에 담긴 Operation을 취소하려면 Operation Object의 `cancel()`을 호출하거나 Operation Queue의 `cancelAllOperations()`를 호출하여 대기열의 모든 연산을 취소하는 방법이 있다.
-   KVO를 사용해 작업 진행 상황을 감시할 수 있다.



## GCD vs Operation Queue

-   Operation Queue에서는 동시에 실행할 수 있는 Operation의 최대 수를 지정할 수 있다.

-   Operation Queue에서는 Operation을 일시 중지, 다시 시작 및 취소를 할 수 있다.

-   Operation Queue에서는 KVO를 사용할 수 있는 많은 [프로퍼티](https://developer.apple.com/documentation/foundation/operation)들이 있다.

    >   isCancelled, isAsynchronous, isExecuting, isFinished, isReady, dependencies, queuePriority, completionBlock

-   GCD는 앞선 기능을 하지 못한니다. Operation Queue를 좀 더 쉽게 쓸 수 있도록 개발한 것으로 좀 더 오버헤드가 있지만 사용하기에 매우 간편하다.

#### When to Use `Operation`

위에서 언급한 의존성을 이용한 작업의 순서를 결정할 수 있는 점이 GCD에게는 없는 강력한 이점 중 하나이다. 즉 어떠한 작업들의 순서를 지정해줄 필요가 있다면 `Operation`을 사용하는 것이 바람직하다. 하지만 짧은 시간안에 수십개의 작업을 생성하야할 경우에는 `Operation`의 내재된 오버헤드로 인한 성능 문제로 이어질 수 있다.

#### When to Use GCD

GCD는 `Operation`을 사용하여 일련의 작업들을 수행하기 위한 코드에 비해 적은 양의 코드로도 같은 행위를 할 수 있다. GCD가 순서가 아예 없는 것은 아니다. 기본적으로 GCD는 FIFO 형태의 하나의 작업 대기열을 갖고 있기 때문에 들어온 순서대로 작업을 처리할 수 있다. 또한 이들을 들어온 순서에 상관없이 Concurrent하게 작업을 진행할 수도 있다. 이렇게 특정 작업의 순서를 지정해주는 것처럼 `Operation`이 갖고 있는 이점을 사용하는 것이 아니라면 GCD를 사용해도 무방하다.



## More

[자세한 설명](https://caution-dev.github.io/ios/2019/03/15/iOS-GCD-vs-Operation-Queue.html)

[1편](https://babbab2.tistory.com/63)

[2편](https://babbab2.tistory.com/64)

[3편](https://babbab2.tistory.com/65?category=831129)

