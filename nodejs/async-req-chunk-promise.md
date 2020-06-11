# reduce 를 사용해 promise 배열 chunk 하여 처리

chunk 하여 묶어낸 2차원 배열을 `chunkedArr` 라 할 때,

```tyepscript
const result = await chunkedArr.reduce((promise: Promise<R[]>, chunk: T)=> {
    return promise.then(async (result: R[])=> {
        const chunkedResult: R[] = await Promise.all(asyncReqFun(chunk));
        return [...result, chunkedResult];
    })
}, Promise.resolve([] as R[]))
```

이런 식으로 chunk 한 만큼만 `Promise.all()` 로 병렬처리를 하고, chunk 단위로는 동기적으로 처리할 수가 있다.
