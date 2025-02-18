# StringUtils (namespace)

### 요약

문자 또는 문자열과 관련된 유틸리티 함수들이 모여있는 네임스페이스

### 정의된 파일 및 위치:

Include/UglyJSONParser/Utils/StringUtils.hpp

### 설명:

UglyJSONParser 라이브러리에서 사용하는 문자 또는 문자열과 관련된 유틸리티 함수들이 모여있습니다.

물론, 사용자도 사용 가능하지만, 라이브러리에서 필요한 사항에 맞게만 기능이 구현되어있기에, 그렇게 쓸모있지는 않습니다.

### 함수들:


<details>
<summary>펼치기/접기</summary>

||CompareString()|
|-|-|
|정의|bool CompareString(const std::string& target, const std::string& key, size_t targetStringStartIndex);|
|설명|target문자열의 targetStringStartIndex 부터 key문자열의 길이에 해당하는 범위의 문자와,<br>key문자열의 시작부터 끝까지의 문자들을 비교하는 함수.|
|매개변수 1|타입:const std::string&<br>key와 같은지 검사할 대상(target)|
|매개변수 2|타입:const std::string&<br>key|
|매개변수 3|타입:size_t<br>target에서 비교를 시작할 문자열의 위치를 가리키는 인덱스|
|반환|타입:bool<br>true: 매개변수 3이 가리키는 지점의 target 문자열로부터 key와 비교한 결과가 같습니다.<br>false: 다릅니다.|

||IsItDigit()|
|-|-|
|정의|inline bool IsItDigit(const char token)|
|설명|입력으로 받은 token이 0~9까지의 범위 안에 있는지 검사합니다.|
|매개변수|타입:char<br>검사할 토큰|
|반환|타입:bool<br>true:범위 안에 있습니다.<br>false:범위 안에 없습니다.|

||IsItOpeningToken()|
|-|-|
|정의|inline bool IsItOpeningToken(const char token)|
|설명|입력으로 받은 token이 여는토큰([,{) 들중 하나인지 검사합니다.|
|매개변수|타입:char<br>검사할 토큰|
|반환|타입:bool<br>true:여는토큰 입니다.<br>false:여는토큰이 아닙니다.|

||IsItClosingToken()|
|-|-|
|정의|inline bool IsItClosingToken(const char token)|
|설명|입력으로 받은 token이 닫는토큰(],}) 들중 하나인지 검사합니다.|
|매개변수|타입:char<br>검사할 토큰|
|반환|타입:bool<br>true:닫는토큰 입니다.<br>false:닫는토큰이 아닙니다.|

||IsItSign()|
|-|-|
|정의|inline bool IsItSign(const char token)|
|설명|입력으로 받은 token이 부호(+,-) 들중 하나인지 검사합니다.|
|매개변수|타입:char<br>검사할 토큰|
|반환|타입:bool<br>true:부호입니다.<br>false:부호가 아닙니다.|

||Contains()|
|-|-|
|정의|inline bool Contains(const std::string& source, const char key)|
|설명|입력으로 받은 문자열이 입력으로 받은 char를 포함하는지 검사합니다.|
|매개변수 1|타입:const std::string&<br>검사할 문자열|
|매개변수 2|타입:char<br>찾을 토큰|
|반환|타입:bool<br>true:포함합니다.<br>false:포함하지 않습니다.|

</details>

## 용도

이 함수들은 UglyJSONParser 라이브러리 내부에서 파싱, JSONTree 빌드같은 작업에서 문자열과 관련된 비교작업을 하기 위해서 만들어졌습니다.

물론, 사용은 가능하지만, 일반적인 상황에서는 사용할 일이 없습니다.

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)