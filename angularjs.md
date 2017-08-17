# Introduction

이 문서는 **AngularJS 1 framework**에 대해 말합니다.

# Project Architecture

[Johnpapa의 Angular 1 Style Guide](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md)를 참조하였습니다.<br>
현재 프로젝트 구조에 맞게 변경하여 작성했습니다. (예를 들어 ```models```)

```bash
www/
    components/
        calendar.directive.js
        calendar.directive.html
        user-profile.directive.js
        user-profile.directive.html
    filters/
        exercise-translate.filter.js
    images/
    lib/
    models/
        child.model.js
    services
        data.service.js
        localstorage.service.js
    sounds/
    templates/
        foo/
            foo.html
            foo.controller.js
            foo.css
        bar/
            bar.html
            bar.controller.js
            bar.css
    app.js
    index.controller.js
    index.css
    index.html
```

- www/
    - 모든 소스 코드는 이 디렉토리 안에서 작성합니다.
- www/components/
    - AngularJS Drective의 View와 Controller 모음입니다.
    - ```모듈이름.directive.js```, ```모듈이름.directive.html``` 네이밍 룰을 따름니다.
- www/filters/
    - AngularJS filter의 모음입니다.
    - ```모듈이름.filter.js``` 네이밍 룰을 따름니다.
- www/images/
    - 프로젝트에 필요한 image resource의 모음입니다.
- www/lib/
    - 다른 라이브러리들의 모음입니다.
- www/models/
    - OOP관점에서 오브젝트들을 명시적으로 객체화한 클래스의 모음입니다.
    - Framework 특성상 AngularJS service로 작성합니다.
    - ```모듈이름.model.js``` 네이밍 룰을 따름니다.
- www/services/
    - AngularJS service의 모음입니다.
    - ```모듈이름.service.js``` 네이밍 룰을 따름니다.
- www/sounds/
    - 프로젝트에 필요한 sound resource의 모음입니다.
- www/templates/
    - 페이지별로 분류한 모듈 모음입니다.
    - 폴더별로 분류하며 각각 contoller, view, css를 포함합니다.
    - ```모듈이름.controller.js```, ```모듈이름.html```, ```모듈이름.css```,  네이밍 룰을 따름니다.
- app.js
    - AngularJS app 모듈입니다.
- index.controller.js
    - 모든 컨트롤러의 부모 컨트롤러입니다.
- index.css
    - 글로벌 스타일을 작성합니다.
- index.html
    - 진입 페이지이며, 모듈 스크립트와 스타일 파일을 임포트합니다.
