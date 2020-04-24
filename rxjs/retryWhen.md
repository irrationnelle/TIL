# rxjs 에서 retry 가 재실행하는 대상

`retry` 나 `retryWhen` 은 파이프라인 상단의 source observable 을 재실행한다.

이게 무슨 의미냐면,

pipe 라인 상단에서 어떤 함수가 값을 처리한 뒤 `of()` 를 사용해서 값을 publish 하면

`retry` 는 그 `of()` 만 재실행을 한다는 이야기이다.

그래서 에러를 `thrownError` 를 return 해서 던진 경우

`retry` 는 그 observable 만 계속해서 재실행한다.

이것을 막기 위해서는 pipe 라인 상단의 함수에서 `of()` 로 값을 발행하지 않고

`new Observable(observer => {})` 를 이용해서 내부에서 `observer.next()` 로 값을 발행하고

예상가능한 에러는 `observer.error()` 로 처리한다.

예상 불가능한 예외는 `try-catch` 문을 사용해서 파이프라인에서 `retry` 나 `catchError` 가 관리할 수 있도록 하고

이 예상 불가능한 예외를 테스트 해보고 싶을 때는 `try-catch` 문에서 명시적으로 `throw` 를 하면된다.
