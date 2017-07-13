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
