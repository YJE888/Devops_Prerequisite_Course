# Node.js
### Node.js vs Spring
|**Spring**|**Node.js**|
|:---:|:---:|
|Java|JavaScript|
|동기식|비동기식|
|안정성과 확장성 뛰어남|빠른 개발과 프로토타입에 적합|
|java 기반의 라이브러리 사용| npm을 통해 수많은 패키지와 모듈 사용|
|복잡한 로직의 앱, 백엔드 서비스|스트리밍 서비스, 경량 및 빠른 API 서버|
|안정적이고 다중 스레드 활용|단일 스레드로 동작하므로, CPU 집중적인 작업에서는 성능이 떨어짐|


&nbsp;
### Node.js 14버전 설치
```
# -s : 정적으로 출력
# -L : 모든 리디렉션 옵션을 따름
# sudo bash - : 다운로드한 스크립트를 관리자 권한으로 실행
$ curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
$ sudo yum install -y nodejs

# 버전 확인
$ node -v
```
&nbsp;
### NPM(Node Package Manager)
- 버전 확인
  ```
  $ npm -v
  ```
- npm 검색
  ```
  $ npm search file
  ```
- npm 설치
  ```
  # 전역적으로 파일 모듈 설치
  $ npm install file -g
  $ npm install file
  $ tree 
    node_modules/
    └── file
        ├── LICENSE
        ├── README.md
        ├── lib
        │   └── file.js
        ├── package.json
        └── tests
            └── file_spec.js
  ```
&nbsp;  
### 모듈(Modules)
- node.js에서의 Built-in Modules 과 External Modules 이 있음
  - 빌트인 모듈
    - Node.js에 기본적으로 포함된 모듈로 Node.js 환경 자체에 내장되어 있음
    - 파일 시스템 조작, 네트워크 통신, 이벤트 처리 및 기타 핵심 작업을 위한 다양한 기능 제공
    - 예) `fs`, `http`, `tls`, `events` 등이 있으며, `/usr/lib/node_modules/npm/node_modules/` 에 위치함
  - 확장 모듈(Third-party 모듈)
    - 개발자나 커뮤니티에 의해 제작된 모듈로, Node.js의 빌트인 모듈 외에 추가적인 기능을 제공하는 모듈
    - npm을 통해 설치하며, 라이브러리, 도구, 프레임워크, 유틸리티 등을 포함
    - 확장 모듈은 `require` 함수를 사용하여 프로젝트에 가져올 수 있음
- 모듈 경로 조회
  ```
  # 전역 설치된 확장 모듈 경로 조회
  $ npm list -g

  # 특정 프로젝트 내의 확장 모듈 경로 조회
  $ npm list
  ```
