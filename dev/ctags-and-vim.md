# ctags 이용해서 definition 참조하기

## universal-ctags 설치

최종적으로 성공한 것이 이 버전이기 때문에 다른 ctags 는 어떤지 잘 모르겠다.

나는 맥북을 사용하기 때문에 mac os 기준으로 설명한다.

```bash
$ brew install --HEAD universal-ctags/universal-ctags/universal-ctags
```

맥북에는 이미 xcode 툴로 ctags 가 설치되어 있어서 universal-ctags 로 설정하기 위해 다음 alias 가 필요하다.

```bash
alias ctags="`brew --prefix`/bin/ctags"
```


## 설정 파일

`universal-ctags` 는 다른 `ctags` 처럼 `~/.ctags` 에 설정을 저장하지 않는다.

대신 `~/.ctags.d/*.ctags` 나  `./.ctags.d/*.ctags` 에 설정을 저장한다. 이거 때문에 많이 헤메었는데 [공식repo](https://github.com/universal-ctags/ctags) 에 있는 내용이다. 역시 공식 문서가 제일 중요하다.

react 작업을 위해 나는 다음과 같이 설정했다.

```
--exclude=node_modules
--exclude=gulp
--exclude=.git
--exclude=*.md
--exclude=*.svg

--map-TypeScript=+.tsx.
```

이 설정이 없으면 `.tsx` 에서 태그를 찾지 못한다는 경고문을 정말 지겹게 본다.

## ctags 적용

이제 프로젝트 루트 폴더에 가서 다음과 같이 실행한다.

```bash
$ ctags -R
```

exclude 옵션 등은 위에 설정에서 지정했으니 따로 필요없다.

이제 vim 을 실행하면 `ctrl + ]` 등으로 definition 으로 이동 가능하다.

안되는 경우

```vim
:set tags=path/to/tags
```

로 실행한다
