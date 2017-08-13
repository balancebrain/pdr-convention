# Introduction

이 문서는 **전반적인 자바스크립트 스타일**에 대해서 말합니다.
따라서 Server-side, Client-side를 따로 구분하지 않습니다.

# Styles

[Google Style Guide](https://google.github.io/styleguide/javascriptguide.xml)를 따릅니다.

다음은 구글 스타일 가이드에서도 중요한 부분을 다룹니다:

0. 들여쓰기는 탭과 공백 혼합 없이 4-space.

0. File name은 모두 소문자를 사용하고 _ , - 를 사용가능하며 그 외의 기호는 사용하면 안된다.

0. {} 사용은 모든 if, else, for, do, while control block 등에 사용한다. 오직 하나의 예외는 ```if (test()) return;``` 과 같이 짧고 return만 있는 경우

0. 모든 statement 뒤에는 semicolon (;) 을 붙인다. 아래와 같이 다른 결과가 나오는 것을 방지 할 수 있다.

    ```javascript
    // return Object
    function foo1() {
        return {
            bar: 'hello'
        };
    }

    // return undefined
    function foo2() {
        return
        {
            bar: 'hello'
        };
    }
    ```
0. Naming Rule 은 다음과 같다.

    ```
    함수 : functionNamesLikeThis
    변수 : variableNamesLikeThis
    클라스 : ClassNamesLikeThis
    ENUM : EnumNamesLikeThis
    메소드 : methodNamesLikeThis
    상수 : CONSTANT_VALUES_LIKE_THIS
    Namespace : foo.namespaceNamesLikeThis.bar
    파일 : filenameslikethis.js or filenames-like_this.js
    ```


# Comments

주석은 코드를 문서화 도구를 이용해 자동으로 문서화 할 수 있는 중요한 요소입니다.

스타일은 [JSDoc](http://usejsdoc.org/about-getting-started.html)을 따르지만
[Google Style Guide](https://google.github.io/styleguide/javascriptguide.xml)에
언급되어 있는 대로 **제한된 Tag**만 사용합니다.
이에 대해서는 [Google Style Guide - Comments](https://google.github.io/styleguide/javascriptguide.xml?showone=Comments#Comments)
단락을 확인하시기 바랍니다.

다음은 [Google Style Guide](https://google.github.io/styleguide/javascriptguide.xml)에
명시적으로 언급되지 않은 부분입니다.

- ```@type```, ```@param``` 등에서의 배열 타입의 표현
    - ```string[]``` -> ```Array.<string>```
    - 2차원 배열인 경우: ```[string, number][]``` -> ```Array.<Array.<string, number>>```

## 주석을 이용한 정적 코딩 하기.

자바스크립와 같은 동적 언어로 프로그래밍하면 에디터에서 타입 힌트를 제공받을 수 없는 치명적인 약점이 있습니다.<br>
다행이도 Visual Studio Code 등 에디터는 **JSDoc**을 이용하여 주석을 작성하면<br>
완벽하진 않지만 타입 힌팅 기능을 이용할 수 있습니다.

### @typedef 이용하여 오브젝트 프로퍼티 표현하기.

함수에서 ```@return {Object}```처럼 오브젝트를 반환하는 경우,
함수를 사용하는 쪽에서는 이 오브젝트가 어떤 이름의 프로퍼티를 가지고 있는지 알 수 없습니다.<br>
해당 함수 코드를 보면 되지만 매번 확인하기에는 여간 고역이 아닐 수 없습니다.

```javascript
/**
 * @param {number} name
 * @param {number} price
 * @return {Object}
 */
function foo(name, price) {
    return {
        name: name,
        price: price
    };
}
```

위와 같이 간단한 함수가 있다고 합시다.<br>
**JSDoc**을 기반으로 하여 주석을 잘 작성하였다면,
에디터에서 ```foo(``` 까지만 타이핑하면 우리는 함수가 필요로 하는 인자를 알 수 있습니다. 하지만 반환 타입은 ```any```로 표현 되겠지요.

<img width="472" alt="screen shot 2017-08-13 at 6 57 36 pm" src="https://user-images.githubusercontent.com/18391559/29248693-575b3c8a-8059-11e7-8df4-7b4dac932efb.png">

위 처럼요.
동적 언어 특성상 이는 어쩔 수 없는 부분입니다.<br>
위 코드는 오브젝트 리터럴을 사용했기 때문에 보다 명확하지만 오브젝트를 담은 변수를 반환했다면
어떤 프로퍼티를 포함하는지 함수를 직접 실행하기 전까지는 알 수 없습니다.

하지만 ```@typedef``` 태그를 사용하면 이 문제를 해결할 수 있습니다.<br>
물론 *이 함수는 해당 포맷으로만 반환됩니다!* 는 약속이 전제가 있어야 합니다.
아쉬운 부분이지만 동적 언어에서 정적 언어처럼 코딩하기 위해선 서로 약속이 되어야 합니다.

위 코드에 주석을 좀 더 추가하여 확인합니다.

```javascript
/**
 * @typedef CustomObject
 * @property {string} name
 * @property {number} price
 */

/**
 * @param {number} name
 * @param {number} price
 * @return {CustomObject}
 */
function foo(name, price) {
    return {
        name: name,
        price: price
    };
}
```

<img width="615" alt="screen shot 2017-08-13 at 7 09 17 pm" src="https://user-images.githubusercontent.com/18391559/29248767-f1b9d7ea-805a-11e7-97bc-2908dbcb6653.png">


훨씬 나아졌습니다. <br>이제 반환값이 어떤 프로퍼티를 가지는 알 수 있습니다.
```foo()``` 함수의 반환값을 저장하면 해당 변수를 사용 할 때 타입과 프로퍼티도 알 수 있습니다.

<img width="618" alt="screen shot 2017-08-13 at 7 12 07 pm" src="https://user-images.githubusercontent.com/18391559/29248787-5847ecf4-805b-11e7-9f74-dfea6fa84898.png">

