# git fast forward 병합

git 에서 병합 할 때 기본 설정으로 fast forward 방식으로 병합한다.

## fast forward 방식이란?

git merge 로 병합을 할 때 master 의 마지막 commit 으로부터 뻗어나간 브랜치가 새로운 commit 을 쌓는 동안 master 브랜치에서 어떤 commit 도 없다면 병합 때 master 커밋은 단순히 병합 대상인 브랜치의 마지막 commit 으로 이동하면 된다. 이게 fast forward 방식이다.

## default 옵션인데 왜 TIL 을 작성하는가?

bitbucket 에서 master 로 병합할 때는 별도로 fast forward 옵션을 설정해주어야 하기 때문이다.
