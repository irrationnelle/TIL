# Vim 이것저것 다뤄보기

## 검색결과 하이라이트 리셋하기

`:noh` 를 입력하면 하이라이트가 사라진다.

## `NERDTree` 에서 새 파일 작성하기

원하는 `node` 에서 `m` 을 입력한 뒤 `Add child node` 를 선택한다.

## ctags 사용해서 definition 이동하기

굉장히 삽질을 많이 했는데 어찌저찌 성공했다

이건 이야기가 길어서 이 [링크](https://github.com/irrationnelle/TIL/blob/master/dev/ctags-and-vim.md)로 대체

## 프로젝트 내부에 키워드 검색

### fzf 설치

```
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'
```

이후에 `:PlugInstall`

### ag 설치

mac os 기준

```bash
brew install the_silver_searcher
```

이렇게 두개가 설치가 완료되면 vim 에서 `:Ag [keyword to search]` 로 검색 가능
