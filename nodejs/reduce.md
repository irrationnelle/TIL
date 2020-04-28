# reduce method 에서 accumulator 에 변수 넣기

보통은 `reduce` method 를 사용할 때 두번째 인자로 전달하는 `accumulator` 에 상수를 넣을 것이다.

`reduce` 의 역할이 아무래도 배열의 형태를 바꾸기 때문에 배열에 없는 값을 다루면 함수형 프로그래밍이 지향하는 바와도 다르기 때문인 거 같은데

어쨌든 accumulator 의 자리에 `let mutableObj` 같은 걸 넣어주면 mutableObj 을 기준으로 reduce 가 작동한다.

## 이런 로직이 필요했던 상황

예를 들어, `let mutableObj` 에서 각 프로퍼티들을 count 할 때, 이미 존재하는 프로퍼티는 reduce 메소드를 호출하는 배열에도 그 프로퍼티가 있는 경우 count 값을 합쳐주고, mutableObj 에는 없는데 배열에는 그 프로퍼티가 있는 경우에는 그 배열의 프로퍼티 count 값을 새롭게 초기화하는 것이다.

그런데 accumulator 를 `{}` 으로 해주면 이게 안 된다.

굳이 이런 식으로 작업해야 할 필요도 없고 혼란을 주는 방식이지만 일단은 기록한다.


