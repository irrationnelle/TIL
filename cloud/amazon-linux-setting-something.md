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

## swap 으로 메모리 보충하기

제일 저렴한 인스턴스를 사용하는 중이라 메모리가 부족해서 `npm i` 을 실행하면 한참 걸리다가 killed 로 프로세스가 죽는 일이 발생한다..

그래서 하드디스크의 일부를 메모리로 사용해주는 작업을 한다.

```bash
$ sudo /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
$ sudo /sbin/mkswap /var/swap.1
$ sudo chmod 600 /var/swap.1
$ sudo /sbin/swapon /var/swap.1
```

## zsh 기본 쉘로 지정하기

```bash
$ sudo yum install util-linux-user
```

위 명령어를 실행해야 `chsh` 를 사용할 수 있다.

```bash
$ chsh -s `which zsh`
```

## vim bootstrap 의 .vimrc 파일 간단하게 받아오기

```bash
curl 'https://vim-bootstrap.com/generate.vim' --data 'editor=vim&langs=javascript&langs=html&langs=typescript&langs=rust&langs=python&langs=c' > ~/.vimrc
```

이 방법을 사용하면 바로 vim 실행 후 `PlugInstall` 로 세팅을 완료할 수 있다.
