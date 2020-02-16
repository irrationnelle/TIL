# sprinig data jps 사용시 equals 메소드 사용

DAO를 사용중이다가 spring data jpa 로 변경하였으면 entity 로 사용 중인 value object 를 유심히 봐야한다.

만약 `equals` 메소드를 `override` 해서 다른 곳에서 사용 중이라면, 그리고 그 `equals` 메소드가 dao 와 관련성이 깊은 경우

다른 비즈니스 로직에서 에러가 날 확률이 높다.

특별히 `equals` 과정에서 무언가 프로퍼티를 넣어줄 게 아니라면 `override`한 함수를 삭제하자.
