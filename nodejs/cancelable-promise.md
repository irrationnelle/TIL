# promise 작업을 취소할 때

[`p-cancelable`](https://github.com/sindresorhus/p-cancelable) 이라는 라이브러리 사용 가능

```typescript
const cancelablePromise = new PCancelable((resolve, reject, onCancel) => {
	let shouldCancel = false;

	onCancel(() => {
        shouldCancel = true;
	});

    if(shouldCancel) return;
});
```

이런 식으로 작업하면 `shouldCancel` 을 이용해서 좀 더 세부적인 위치에서 오퍼레이션 수행을 중단하고 취소할 수 있다.
