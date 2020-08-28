# selenium 테스트를 Travis CI 환경에서 할 때 

- `mocha-example` 에 PR 을 보냈고 피드백을 받아서 반영한 뒤 다시 PR 을 보냈더니 이전에는 통과했던 Travis CI 가 통과하지 않았다.

- 확인해보니 내 PR 문제는 아니고 기존에 있던 `selenium` 예제에서 `chromedriver` 가 v83 기준이었는데 Travis 에서는 `stable` 아니면 `beta` 로만 버저닝이 가능해서 v85 가 설치되어 생긴 것

- 일단 트리키한 방법이 있을지는 몰라도 Travis 공식문서 자체에서는 버저닝은 `stable` 만 가능하다고 하니까 매번 `selenium` 의 `chromedriver` 버전을 업그레이드 해주어야 한다.   