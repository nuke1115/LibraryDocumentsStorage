# TypeUtils (namespace)

### 요약

타입과 관련된 유틸리티 함수들이 모여있는 네임스페이스

### 정의된 파일 및 위치:

Include/UglyJSONParser/Utils/TypeUtils.hpp

### 설명:

UglyJSONParser 라이브러리에서 사용하는 타입과 관련된 유틸리티 함수들이 모여있습니다.

물론, 사용자도 사용 가능하지만, 라이브러리에서 필요한 사항에 맞게만 기능이 구현되어있습니다.

따라서, 그렇게 쓸모있지는 않습니다.

### 함수들:

||ConvertStringToBool()|
|-|-|
|정의|inline bool ConvertStringToBool(const std::string& data)|
|설명|string 타입의 매개변수를 bool로 변환해 반환합니다.|
|<span style="color:red">주의</span>|입력은 토큰화를 거친 문자열이라고 가정합니다.|
|매개변수|const std::string&<br>bool로 바꿀 문자열|
|반환|타입:bool<br>true:매개변수가 (true)와 같을때<br>false:매개변수가 (true)가 아닐때|

||ConvertBoolToString()|
|-|-|
|정의|std::string ConvertBoolToString(bool data);|
|설명|bool타입의 매개변수를 string으로 변환해 반환합니다.|
|매개변수|타입:bool<br>문자열로 바꿀 bool|
|반환|타입:std::string<br>(true):매개변수가 true일때<br>(false):매개변수가 false일때|

||IsItJsonBool()|
|-|-|
|정의|inline bool IsItJsonBool(const std::string& key)|
|설명|입력으로 들어온 문자열이 json의 bool과 같은지 검사해 결과를 반환합니다.|
|<span style="color:red">주의</span>|입력은 토큰화를 거친 문자열이라고 가정합니다.|
|매개변수|타입:const std::string&<br>검사할 문자열|
|반환|타입:bool<br>true:문자열이 (true) 또는 (false)일때<br>false:문자열이 (true)(false)둘 다 아닐때|

||IsItJsonString()|
|-|-|
|정의|inline bool IsItJsonString(const std::string& key)|
|설명|매개변수로 들어온 문자열의 양 끝에 (")이 있는지 검사한 뒤, 결과를 반환합니다.|
|<span style="color:red">주의</span>|입력은 토큰화를 거친 문자열이라고 가정합니다.|
|매개변수|타입const std::string&<br>검사할 문자열|
|반환|타입:bool<br>true:있을때<br>false:없을때|

||IsItSingleJsonValue()|
|-|-|
|정의|inline bool IsItSingleJsonValue(const std::string& key)|
|설명|매개변수로 들어온 문자열이 json의 null,bool,number,string 인지 검사한 뒤, 결과를 반환합니다.|
|<span style="color:red">주의</span>|입력은 토큰화를 거친 문자열이라고 가정합니다.|
|매개변수|타입:const std::string&<br>검사할 문자열|
|반환|타입:bool<br>true:맞을떄<br>false:아닐때|

||GetNodeTypeOfToken()|
|-|-|
|정의|NodeType GetNodeTypeOfToken(const std::string& token);|
|설명|입력받은 문자열을 검사하여, 문자열 타입과 일치하는 노드의 타입을 반환합니다.|
|매개변수|타입:const std::string&<br>검사할 문자열|
|반환|타입:UglyJSONParser::NodeType<br>받은 토큰에 해당하는 노드의 타입|

## 용도

이 함수들은 UglyJSONParser 라이브러리 내부에서 파싱, JSONTree 빌드같은 작업에서 타입과 관련된 작업을 하기 위해서 만들어졌습니다.

물론, 사용은 가능하지만, 일반적인 상황에서는 사용할 일이 없습니다.

## <span style="color:red">주의</span>

이 네임스페이스의 함수들의 인자로 받는 문자열들은, **모두 토큰화와 검증과정을 거친 문자열**이라는 가정 하에 작성되었습니다.

잘못된 json문법의 문자열이 입력될시, 정상적인 작동을 보장할 수 없습니다.

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)