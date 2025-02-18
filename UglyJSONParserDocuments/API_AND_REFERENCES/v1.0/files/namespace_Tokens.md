# Tokens (namespace)

### 요약

JSON 토큰화에 필요한 상수들이 모여있는 네임스페이스

### 정의된 파일 및 위치:
Include/UglyJSONParser/Tokenizer/Tokens.hpp

### 설명:

문자열을 JSONTreeBuilder에서 사용 가능한 토큰들로 토큰화할 때, Tokenizer에서 사용하는 상수들의 집합입니다. 

## 상수들

<details>
<summary>펼치기/접기</summary>

|토큰 이름|설명|
|-|-|
|TokenTrue|JSON의 true를 문자열 토큰으로 변환한것|
|TokenFalse|JSON의 false를 문자열 토큰으로 변환한것|
|TokenNull|JSON의 null을 문자열 토큰으로 변환한것|
|TokenQuotationMark|JSON의 문자열의 시작과 끝을 감싸는 (")를 문자 토큰으로 변환한것|
|TokenObjectStart<br>TokenObjectEnd|JSON의 Object의 열고 닫는 문자를 토큰으로 변환한것.<br>여는것 : ({)<br>닫는것 : (})|
|TokenArrayStart<br>TokenArrayEnd|JSON의 Array의 열고 닫는 문자를 토큰으로 변환한것.<br>여는것 : ([)<br>닫는것 : (])|
|TokenComma|쉼표(,)를 문자 토큰으로 변환한것|
|TokenPlus<br>TokenMinus|부호(+,-)를 문자 토큰으로 변환한것|
|TokenColon|콜론(:)을 문자 토큰으로 변환한것|
|TokenBackslash|백슬래시(\) 를 문자 토큰으로 변환한것.|
|NumRangeStart<br>NumRangeEnd|ASCIICode에서의 숫자 범위의 시작(0)과 끝(9)을 문자 토큰으로 변환한것|
|TokenDecimalPoint|소수점(.)을 문자 토큰으로 변환한것|
|TokenExponentUpper<br>TokenExponentLower|지수 기호(E,e)의 대문자와 소문자를 문자 토큰으로 변환한것|
|TokenSpace|스페이스 문자를 문자 토큰으로 나타낸것|
|TokenLineFeed|(\n) 을 문자 토큰으로 나타낸것|
|TokenCarriageReturn|(\r)을 문자 토큰으로 나타낸것|
|TokenHorizontalTab|(\t)를 문자 토큰으로 나타낸것|

</details>



## 용도

이 상수들은 UglyJSONParser의 Tokenizer에서 사용하기 위해 정의되었습니다.

토크나이저를 사용자가 다시 작성하려고 하지 않는이상, 이 상수들을 직접 사용할 일은 없습니다.

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)