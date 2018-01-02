# Introduction

이 문서는 **전반적인 DataBase 스타일**에 대해서 말합니다.

# Naming Rules
Table과 Coulmn Name에 대한 규칙을 설명한다.

### 공통

*  이름은 명사로 작명한다. 동사는 사용하지 않는다.
*  이름은 단수형으로 작명한다.

---

0. Table Name
    * 테이블 이름은 Upper camel case 로 한다.
    ```
    ex)
      UserInfo
    ```
    * 부모 자식 관계 테이블에 경우 자식은 부모의 이름을 물려 받는 것을 권장한다.
    ```
    ex)
      부모: UserInfo
      자식: UserInfoMember
          UserInfoNonmember
    ```
0. Column Name

    * 컬럼 이름은 Lower Camel Case 로 한다.
    ```
    ex)
      userCode
    ```

### 예약어
Table 과 Column의 Naming에 대한 예약어 입니다.

| 분류  | 예약어 | 부가 설명                                      |
|------|------|----------------------------------------------|
|Number| num | Number type의 컬럼 이름을 지을 경우 사용 할 수 있습니다.|
