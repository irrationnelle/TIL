# immutable 을 지향하자

react 에서 re-render 를 하는 기준은 참조값이다. 그래서 변수들을 immutable 하게 사용하는 게 중요하다.

오늘 코드 리뷰에서 splice 로 값을 mutable 하게 변경하고 그 배열을 spread operator 를 이용하여 새로운 배열로 만든 뒤 re-render 를 하는 방식을 사용했는데

해당 방식은 mutable 한 값변화가 있으니 부수효과가 우려된다고 리뷰를 받았다.

그래서 spread operator 가 있는데 왜 mutable 하느냐고 반박했는데

re-render 를 하는 부분이 문제가 아니라

값이 변한 그 배열을 바라보고 있는 곳이 있다면, mutable 하게 바뀐 값으로 이해 부수효과가 발생할 수 있다고 하였다.

그러니 splice 보다는 filter 를 쓰도록 하자.

참고로 filter 는 순서 보장이 된다고 한다. 
