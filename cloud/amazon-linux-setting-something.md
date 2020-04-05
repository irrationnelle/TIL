# AWS 의 amazon linux 에 개발환경 세팅하기

주말동안 심심해서 오랜만에 이전에 만든 lightsail 인스턴스에 접속해서 설정했다.

## zsh 최신 버전 설치하기

`centos` 와는 또 달리 `amazon linux` 에서는 `zsh` 가 `5.0.2` 버전이 최신 버전으로 리포지토리에 등록된 것 같다.

제일 간단한 방법으로 직접 zsh 리포에서 소스코드를 받아서 빌드했다.

우선 빌드를 위해 필요한 의존성들을 설치한다.

```bash
$ sudo yum install -y git make ncurses-devel gcc autoconf man yodl
```

이후 순차적으로 다음 명령어들을 실행한다.


```bash
$ git clone -b 5.9 https://github.com/zsh-users/zsh.git /tmp/zsh
$ cd /tmp/zsh
$ ./Util/preconfig
$ ./configure
$ sudo make -j 20 install
$ /usr/local/bin/zsh --version
$ zsh
$ chsh -s /usr/local/bin/zsh
```

그러면 5.9 버전이 아니라`zsh 5.8.0.1-dev (x86_64-pc-linux-gnu)`이 설치되어있다. 뭐여.

## vim 최신 버전 설치하기

하는 김에 vim 도 직접 빌드해서 설치해보자.

```bash
$ git clone https://github.com/vim/vim.git
$ cd vim
$ sudo ./configure --enable-pythoninterp --with-python-config-dir=/usr/lib/python2.7/config
$ make -j8
$ sudo make install
```

중간에 `./configure` 로 시작하는 명령어를 실행해주지 않으면 나중에 `UltiSnips requires py >= 2.6 or any py3` 라는 짜증스러운 메시지를 볼 수 있다.

## ctags 최신 버전 설치하기

개발환경 구축을 위해 ctags 도 설치한다.

```bash
$ sudo yum install -y automake
$ git clone https://github.com/universal-ctags/ctags.git
$ cd ctags
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
$ ctags --version
```

`automake` 가 사전에 설치되어 있지 않으면 `./autogen.sh` 에서 에러가 발생한다.
