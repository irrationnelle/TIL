# <span> 태그에서 텍스트 줄바꿈하기

우선 enter 를 쳐서 문단을 나눈 것이 아닌 경우 줄바꿈이 안 될 때가 있다.

이 경우에는, `word-break: "break-all"` 을 주면 width 값에 맞춰서 줄바꿈이 된다.

또, `white-space` 설정에 따라 줄바꿈을 하지 않고 태그를 뚫어버리거나, 가로 스크롤이 생기는 경우가 생길 수 있다.

이 때는 `white-space: pre-line` 으로 설정한다.

