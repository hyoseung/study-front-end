# Package Manager

## NPM

* Node Package Manager
* 유용한 자바스크립트 패키지들을 만들어두고 코드가 공개되어있음
* npm에 업로드된 노드 모듈을 패키지라고 부름
* npm으로 외부 모듈 설치할 경우 node_modules 디렉토리에 저장

## package.json

설치한 패키지들을 관리하는 파일

## yarn

* Facebook에서 개발한 Javascript의 새로운 패키지 매니저
* 다운받은 패키지 데이터를 캐시(cache)에 저장하여, 중복된 데이터는 다운로드하지않고, 캐시에 저장된 파일을 활용함으로써 패키지 설치속도가 매우 빠름

## npm, yarn 명령어 비교

| 기능                     | npm                              | yarn                            |
| ---------------------- | -------------------------------- | ------------------------------- |
| package.json 생성        | npm init                         | yarn init                       |
| package.json 패키지 설치    | npm i                            | yarn install                    |
| 패키지 전역 설치              | npm i -g \<package-name>         | yarn add global \<package-name> |
| dependancy에 패키지 설치     | npm i \<package-name>            | yarn add \<package-name>        |
| devDependancy에 패키지 설치  | npm i \<package-name> --save-dev | yarn add \<package-name> --dev  |
| 패키지 삭제                 | npm uninstall \<package-name>    | yarn remove \<package-name>     |
| 모든 라이브러리를 최신 버전으로 업데이트 |                                  | yarn upgrade --latest           |

* dependencies : 배포용 라이브러리
* devDependencies : 개발용 라이브러리

## 출처

* [ooeunz | 2019. 10. 11. 11:07 | \[Node.js\] npm이란?](https://ooeunz.tistory.com/19)
* [gwak2837 | 2020년 2월 11일 | yarn 사용법 (npm과 비교)](https://velog.io/@gwak2837/Node.js-%EA%B4%80%EB%A0%A8-%EC%83%81%EC%8B%9D)
*   [Damien.Lee     \| 2020. 12. 8. 16:30 | NPM? Yarn? , 본인에게 편한게 최고!](https://dark0946.tistory.com/419)

