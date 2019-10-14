# 인스턴스를 다루는 Observable

```typescript
class Test {
    num = 0;
    
    increment = () => {
        this.num++;
    }
}

const obsA = of(new Test());

obsA.subscribe(result => {
    result.increment();
})


setTimeout(() => {
    obsA.subscribe(result => {
        console.debug(result.num);
    });
}, 500);
```

* 결과는 1이 나온다. 두 개의 구독에서 나오는  `result` 가 동일한 인스턴스임을 알 수 있다.
* 그래도 의심스럽다면 `===` 연산으로 비교해서 확인이 가능하다.
* 하지만 클래스 메소드를 호출하여 클래스 멤버변수에 수정을 가했기 때문에 부수효과로 인한 위험이 생긴다.
    * 따라서 `깊은 복사` 를 하여 새로운 인스턴스를 obsA에 발생시켜주는 등 관리가 필요하다.
     
