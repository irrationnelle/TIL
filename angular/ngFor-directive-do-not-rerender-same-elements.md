# angular2+ 에서 ngFor directive 로 동일한 elements 는 re-rendering 하지 않기

angular 에서는 `*ngFor` 라는 directive 를 이용해서 마치 js에서 `for..of` 를 쓴 것처럼 컴포넌트를 반복적으로 렌더링이 가능하다.

그런데 이 반복문을 실행하기 위한 배열이 갱신될 때 마다 배열 요소에 해당하는 각 컴포넌트들이 전부 동시에 리렌더링이 발생한다.

여기서 이미 rendering을 완료하였고 먼저 렌더링했던 배열의 요소와 동일한 배열 요소라고 하면 리렌더링을 하지 않고 그대로 두는 방법이 있다.

`trackBy` 라는 키워드를 `*ngFor` directvie 와 함께 사용하는 방법이다.

`trackBy` 는 angular 컴포넌트 클래스의 메소드인데 다음과 같이 사용한다.

```typescript
// angular 컴포넌트 클래스 내부의 메소드이다.
trackByItem(index: number, item: Item) {
    return !item ? null : item.id;
}
```

그 후 angular 컴포넌트 html 에 다음과 같이 명시한다.

```html
<div *ngFor="let item of items; trackBy: trackByItem"></div>
```

이렇게 하면 이제 추가되거나 변경되는 배열 요소에 한정하여 리렌더링을 수행한다.

주로 성능 개선을 위해 이 방법을 사용하지만 내 경우 아무리 리렌더링이 빨라도 이미 존재하는 요소들이 다시 랜더링 되면서 깜빡이는 것이 보기 싫다고 하여 적용한 것이었다.
