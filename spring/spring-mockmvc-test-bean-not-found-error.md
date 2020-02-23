# Mock mvc 를 이용해서 webmvc controller 테스트를 하고 싶은 상황

`spring rest docs` 를 사용해서 테스트를 통과하면 자동으로 문서화를 진행하기 위해

지금까지는 `WebTestClient` 를 이용하다가 `MockMvc` 를 이용한 컨트롤러 테스트를 진행하려고 했다.

# bean 을 찾을 수 없다는 에러

```bash
***************************
APPLICATION FAILED TO START
***************************

Description:

Parameter 1 of constructor in atdd.path.web.UserController required a bean of type 'atdd.path.auth.JwtTokenProvider' that could not be found.


Action:

Consider defining a bean of type 'atdd.path.auth.JwtTokenProvider' in your configuration.
```

위와 같은 에러가 발생한다.

# spring 에서 bean 을 DI(Dependency Injection) 하기 위해 필요한 것들

지금까지는 어설프게 코드를 작성해도 spring 이 똑똑하게 DI를 다 해주었는데 이 기회에 자세히 알아보니 생각보다 신경 써주어야 하는 것들이 꽤 있었다.

- `@Component` 나 `@Service` 등의 어노테이션 선언해주기

  - 매우 당연하지만 spring framework 는 워낙 방대해서 그런지 프레임워크라기 보단 일종의 언어라는 느낌이 강해서 그런가 그냥 알아서 DI를 해줄 것이라는 막연한 기대(?)가 있다.

  - 하지만 spring 입장에선 클래스나 프로퍼티들을 bean 으로 다뤄야 할지 어떨지 알 수가 없으므로 이런 어노테이션 추가를 해주어서 `ApplicationContext` 가 알 수 있도록 해주어야 한다.

- 매개변수를 선언하지 않은 빈 생성자 만들기

  - 이 부분은 spring 3 에서 `@Configuration` 어노테이션을 사용할 때는 필요하다고 된 것을 공식문서에서 확인했는데 그 후에는 찾아볼 수가 없어서 잘 모르겠다. 일단 나 또한 매개변수가 없는 빈 생성자, 즉 기본 생성자(`default constructor`)를 만들지 않고서도 사용했으니까.

# 그래도 안 된다.

지금까지 잘 되다가 왜 갑자기 `ApplicationContext` 가 bean 을 찾지 못 하는 걸까,

이것저것 다 시도해보다가, 한 가지 알게 된 점이 있었다.

> `WebTestClient` 를 이용한 테스트에서는 bean 을 찾는데 `MockMvc`를 이용한 테스트에서는 bean 을 찾지 못한다.

즉 JwtTokenProvider 클래스 자체의 문제가 아니라 `MockMvc` 와 관련이 있는 이슈가 아닐까?

# `@MockBean` 으로 해결

[이 답변](https://stackoverflow.com/a/47330050) 을 보면 다음과 같이 이야기한다.

> @WebMvcTest is only intended to test your controllers, and won't load all your app's beans at all

그러니까 Controller 를 제외하면 bean 을 주입하지 않는 것이다. 그러니 당연히 에러가 발생하지.

결국 `@MockBean` 으로 JwtTokenProvider 를 주입하는 것으로 해결했다.

거의 반나절을 이걸로 고생했는데 정작 해결법은 이렇게 쉽다.
