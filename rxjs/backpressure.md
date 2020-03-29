# 배압 ( backpressure ) 정리

spring 으로 reactive 아키텍처를 구성하는 책을 보다보니 backpressure 에 대한 이야기가 나와서 정리한다.

## backpressure 란?

간단하게 말해서 production 의 속도가 consumer 의 속도보다 빠른 것을 의미한다.

reactive stream 에서 위의 이야기를 대입하면

source observable 이 발행하는 속도가 subscription observer 가 구독하는 속도보다 빠른 것을 의미한다.

이런 backpressure 상황 자체가 문제라기 보단, backpressure 일 때 subscription observer 가 수행하는 작업들이 문제를 일으킬 가능성이 높다.

예를 들어 subscription observer 가 자원을 많이 소모하고 시간이 오래 걸리는 작업을 한다고 할 때, subscription observer 는 작업이 끝나자마자 다시 source observable 로부터 받은 작업을 수행한다. node js 의 v8 엔진은 가비지 컬렉터가 메인 스레드에서 같이 움직이기 때문에 이런 쉴틈없는 작업은 가비지 컬렉션의 수행을 막을 수 있다. 따라서 앱이 완전히 터져버리는 수도 있다.

## backpressure 를 관리하는 방법

### lossy 한 수단

- debounce / throttle 사용한다. 이 방법이 lossy 한 방법인 이유는 production 중 일부는 무시하는 전략이기 때문이다. 예를 들어 3초에 한 번씩 comsume 하겠다고 결정한다면 1초마다 produce 하는 경우 3개 중 2개는 무시한다.

### loseless 한 수단

- buffer 를 사용한다. 즉, consumer 가 처리를 완료할 때까지 buffer 쪽에서 저장을 하는 개념이다. 이 전략의 경우 heap 메모리가 터질 수 있다.
