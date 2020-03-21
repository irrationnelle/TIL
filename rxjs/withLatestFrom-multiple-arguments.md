# `withLatestFrom을 이용해서 다중 인자 받기`

rxjs 의 파이프라인 중에서 `withLatestFrom` 을 사용해야 할 때

매개변수 자리에 2개 이상의 인자를 전달하면

다중인자를 받을 수 있다.

이런 식으로 한 뒤 만약 인자의 옵저버블이 각각 string, string 타입을 가진다면

```typescript
of(1).pipe(
  withLatestFrom(of('a'), of('b'))
).subscribe(([first, second]: [string: string])=> {
  console.log(first);
  console.log(second);
})
```

이런식으로 다룰 수 있다.
