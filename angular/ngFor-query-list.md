# ngFor directive 가 있는 컴포넌트에서 ref 접근하는 방법

angular 에서 ref 접근하는 방법 중 `@ViewChild` 를 사용하는 방법이 있다.

그런데 `@ViewChild` 로는 `ngFor` directive 로는 애매하기 때문에

`@ViewChildren` 을 사용해서 `QueryList` 로 다루는 것이 좋다.

그런데 만약 ngFor 의 element 가 ngIf directive 와 함께한다면 자식 컴포넌트를 별도의 컴포넌트로 만든 뒤

해당 자식 컴포넌트가 AfterViewInit 를 상속하고 `ngAfterViewInit` 라이프 사이클을 이용하는 것이 낫다.
