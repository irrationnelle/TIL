# mvc controller 에서 `status code` 의 주의점

`DELETE` 요청 같은 경우 삭제가 정상적으로 이루어질 경우에는 `no content` 응답을 주지만, `GET` 요청에서는 해당하는 아이템이 없는 경우 `not found` 를 응답하도록 했다.

그런데 이게 테스트에서 복병처럼 작용하는 점이,

`uri` 가 잘못된 경우에도 404 에러가 발생하는데, 적절한 mocking 을 해주지 않아서 `GET` 요청에 해당하는 아이템이 없을 때에도 404 가 발생한다.

그래서 테스트에서 `uri` 가 존재하지 않는 것인지 mocking 환경설정에 대한 문제인지 파악이 어려운 경우가 생겼다.

고민해볼 필요가 있음.

# 로그인하여 응답으로 jwt token 을 받는 경우 다음과 같은 mocking 이 필요하다.

```java
    given(userRepository.findByEmail(any())).willReturn(Optional.of(user));
    given(jwtTokenProvider.createToken(any())).willReturn(TEST_USER_TOKEN);
```

어느 한쪽의 mocking 도 빼먹는 경우, `204` 나 혹은 `token` 을 받지 못한다는 에러가 발생한다.

그래서 둘을 동시에 mocking을 꼭 해주어야 합니다
