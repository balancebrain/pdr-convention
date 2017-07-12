# PDR Javascript Style Guide

0. 들여쓰기는 탭과 공백 혼합 없이 4-space.

1. File name은 모두 소문자를 사용하고 _ , - 를 사용가능하며 그 외의 기호는 사용하면 안된다.

2. {} 사용은 모든 if, else, for, do, while control block 등에 사용한다. 오직 하나의 예외는 ```if (test()) return;``` 과 같이 짧고 return만 있는 경우

3. 모든 statement 뒤에는 semicolon (;) 을 붙인다. 아래와 같이 다른 결과가 나오는 것을 방지 할 수 있다.

```
    function foo1()
    {
        return {
            bar: "hello"
        };
    }

    function foo2()
    {
        return
        {
            bar: "hello"
        };
    }
```