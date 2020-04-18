# CRA ( Create React App ) 사용시 .env 사용법

`REACT_APP_` 로 변수명을 시작해야 CRA 가 자동으로 `.env` 의 변수값을 읽어온다.


변수명을 그냥 마음대로 지으면 CRA 가 읽어오지 못해서 `dot-env` 등을 설치하거나 해야함.


# public 디렉토리 내부의 index.html 에서 env 값 사용

변수값 앞 뒤로 `%` 를 추가한다.

예를 들어 `REACT_APP_KAKAO_MAP_API_KEY` 가 변수명이라면

`%REACT_APP_KAKAO_MAP_API_KEY%` 로 사용하면

빌드 시점에서 원하는 값이 들어간다.
