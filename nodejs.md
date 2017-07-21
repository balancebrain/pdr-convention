# Introduction

이 문서는 **Node.js를 이용하는 웹 스택 프로젝트**에 대해 설명합니다.

# Restriction

- Web Server Framework로 [Express.js](http://expressjs.com/ko/)를 사용합니다.
- RESTFul API를 지향합니다.

# Project Architecture

```bash
src/
    config/
    controller/
    dao/
    middleware/
    models/
    routes/
    util/
test/
.gitginore
index.js
package.json
README.md
```

- src/
    - 모든 소스 코드는 이 디렉토리 안에서 작성합니다.
- src/config/
    - 시스템 설정에 대한 소스 코드를 저장합니다.
    - DB Connection 정보. 시스템 실행 환경 등이 포함됩니다.
- src/controller/
    - 컨트롤러는 하나의 트랜잭션을 의미합니다.
    - router와 직접 연결되어 있으며, router에 대한 동작은 컨트롤러에서 합니다.
    - 오직 컨트롤러만이 Dao를 호출할 수 있습니다.
- src/dao/
    - Data Access Object의 약자입니다.
    - DAO만이 Query를 전송할 수 있습니다.
    - 쿼리문과 PacketDataRow에 대한 Mapping을 수행합니다.
    - PacketDataRow는 node-mysql의 데이터 정보를 가진 객체입니다.
- src/middleware/
    - express의 middleware입니다.
    - Session 검사, http header 등 모든 라우터에 공통적으로 하는 일을 수행합니다.
- src/models/
    - 시스템 로직을 가진 객체입니다.
    - OOP에서는 객체들의 관계로 도메인을 주도합니다.
    - 디자인 패턴으로 나타낼 수 있습니다.
    디자인 패턴은 알려진 문제를 해결하고 개발자간 커뮤니케이션을 유연하게 할 수 있는 요소입니다.
- src/routes/
    - 각 API URL은 여기에 파일로 나타납니다.
    - API Parameter 유효성을 검사하고 컨트롤러에 넘겨줍니다.
- src/utils/
    - 특정 클래스에 종속되지 않는 클래스입니다.
    - 배열을 특정 크기로 잘라 주거나 맵에서 값으로 키 값을 찾아주는 클래스 등
    유용한 클래스를 만들 수 있습니다.
- test/
    - 테스트 코드는 여기에 작성합니다.
- index.js
    - 시스템의 Entry Point입니다.
- package.json
    - npm 모듈 의존성 관리 및 프로젝트 정보를 저장하는 파일입니다.
- README.md
    - 프로젝트 정보를 나타내는 Markdown 파일입니다.
    - 간단하게 나마 어떤 일을 하는 프로젝트인지 작성해야 합니다.
    - 빌드 또는 실행 방법을 설명해야 합니다.
