# alpine linux 에 대하여

작업 중인 토이 프로젝트에 CI/CD 를 적용시키려다 Docker 까지 다루게 되었다.

그런데 Docker 이미지 생성 단계에서 `alpine` 이라는 키워드가 자주 보여서 이게 뭔가 찾아보았다.

공식 홈페이지의 소개 문구를 보자면

> Small. Simple. Secure.
> Alpine Linux is a security-oriented, lightweight Linux distribution based on musl libc and busybox.

즉 초경량의 단순하지만 어느 정도의 보안책을 구비한 리눅스 배포판이라는 것을 알 수 있다.

패키지 관리자로 [`apk`](https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management) 라는 걸 사용한다고 한다.

## 아무래도 좋은 이야기

여담으로 난 맥북을 사용하지만 만약 개발용 및 일반 사용자용으로 리눅스 배포판을 고르라면 우분투를 선호하는 편인데,

fedora 나 centos 는 개발용 및 일반 사용자용으로 쓰기에는 repository 관리도 해주어야 하고 우분투에 비해 직접 바이너리를 컴파일해서 사용해야 하는 것들이 많기 때문이다. 대신 fedora 최신 버전을 사용하면 arch linux 만큼은 아니나 나름 최신 트렌드를 반영한 리눅스를 사용한다는 짜릿함(?)은 있다.
