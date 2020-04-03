# Homebrew 에서 permission 관련 문제가 발생할 때

```bash
sudo chown -R $(whoami) $(brew --prefix)/*
```

맥북에서 사용자를 하나 더 추가해서 사용 중인데 두 계정을 번갈아가며 쓰니 permission 관련 에러가 자주 발생한다.

왜 관리자 계정으로 하나 더 생성한 것인데 이렇게 귀찮은 작업이 많은지는 모르겠음.
