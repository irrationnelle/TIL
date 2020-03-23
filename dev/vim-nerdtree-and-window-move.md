# Vim 에서 NERDTree 사용하기

TIL 을 작성할 때는 주로 vim 을 사용하는 편인데 평소에 IDE에서 vim plugin 을 사용하기 때문에 어느 정도 손에 익은 것도 있고

짤막하게 작성하는 편인데 IDE 를 실행시키는 것도 굼뜬 느낌이 들어서이다.

이왕 VIM 을 사용하는 김에 IDE처럼 사용해보는 방법을 연구해보고자 한다.

먼저 파일 탐색 기능인 `NERDTree` 를 사용하는 방법이다.

나는 [Vim-Bootstrap](https://vim-bootstrap.com/) 을 사용하기 때문에 `NERDTree` 가 이미 설치되어 있지만 설치 방법부터 알아보자.

## 터미널 설치방법

[The NERDTree](https://github.com/preservim/nerdtree) 에서 나온 방법 중 가장 편한 방법은 다음처럼 터미널에서 입력하는 방법이다.

```bash
git clone https://github.com/preservim/nerdtree.git ~/.vim/pack/vendor/start/nerdtree
vim -u NONE -c "helptags ~/.vim/pack/vendor/start/nerdtree/doc" -c q
```

그런데 이 방법은 vim 8버전 이상을 사용해야 유효한 방법이라 한다.

## Vim-plug 설치 방법

```bash
vim ~/.vimrc
```

로 들어가서 다음과 같이 입력한다.

```
call plug#begin()
Plug 'preservim/nerdtree'
call plug#end()
```

그 후 vim 실행 후 `:PlugInstall` 로 실행

## 실행 방법

`:NERDTree` 로 실행하면 나온다. 단축키 설정하는 방법도 있지만 vim 자체를 그렇게까지 자주 쓰진 않기 때문에 패스

실행 후 다시 편집하는 영역으로 옮기기 위해선 맥 기준으로 `Ctrl + w + w` 이다.


