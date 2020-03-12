# pipe 와 innerHtml 을 이용해서 동적 텍스트에 일부만 bold 효과 주기

텍스트 일부에만 볼드 효과를 주는 것은 간단하다. 그냥 그 사이에 `<strong></strong>` 만 삽입해주면 된다.

그런데 그 텍스트가 동적 텍스트라면 `<strong></strong>`을 넣어주기가 곤란해진다.

예전에는 `<span>` 을 여러번 사용해서 굉장히 번거롭게 처리했는데,

문득 angular 에서 지원하는 방법이 따로 있을 것이라 생각했다.

## innerHtml 프로퍼티

angular 컴포넌트에서 `[innerHtml]` 프로퍼티를 이용하면 text 대신에 html 태그를 삽입이 가능하다.

그럼 동적 텍스트에서 단순히 string 만 작성하는 것이 아니라 해당 string 에 `<strong></strong>` 같은 걸 감싸주도록 하면 된다.

## sanitizer

그런데 이 방법이 보안에 별로 좋지 않은 방식이라서 angular 쪽에서 단순히 `[innerHtml]` 만 사용한다고 쓸 수는 없다고 한다.

그럴 땐 이 [블로그](https://blog.eunsatio.io/develop/Angular-2%2B-innerHTML%EC%97%90%EC%84%9C-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EC%8A%A4%ED%83%80%EC%9D%BC%EC%9D%B4-%EC%97%86%EC%96%B4%EC%A7%88-%EB%95%8C) 에서 알려준 방식대로 sanitizer 를 이용하자.

해당 블로그의 내용은 그대로 옮기면 의미가 없기 때문에 `DomSanitizer` 라는 키워드만 여기에 남겨둔다.

이 블로그에서는 인라인 스타일이나 클래스 등의 어트리뷰트들이 모두 사라진다고 했는데

스택오버플로우 등을 참조하면 `innerHtml` 사용에 제약이 많은 듯 하여 첫줄처럼 단순히 `[innerHtml]` 만 사용할 수는 없다고 생각했다. 실제로 그러한지는 테스트가 필요하다.
