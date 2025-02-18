# JSONParser(class)

### 요약:

JSON파일을 읽거나 쓰고, JSONTree를 빌드하는 일련의 과정을 편하게 사용하는것을 도와주는 클래스

### 정의된 파일 및 위치 :

Include/UglyJSONParser/JSONParser/JSONParser.hpp

### 설명 :

JSONParser는 UglyJSONParser의 JSON을 읽고,쓰고,JSONTree를 빌드하는 일련의 기능을 편하게 사용 가능하게 해줍니다.

이를 위해 각 기능을 담당하는 클래스들을 멤버로 가지며, 이들을 각 순서에 맞게 호출하는 함수들을 가지고 있습니다.

이 클래스로 인해, 사용자는 어떤 함수를 어떤 타이밍에 호출하고, 어떤 임시변수가 필요한지 신경쓰지 않아도 됩니다.

## 멤버들:

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

|| JSONParser()|
|-| -|
|특징 | 기본 생성자|

||JSONParser(const JSONParser&)|
|-| -|
|특징 | 기본 복사생성자|

||JSONParser(JSONParser&&)|
|-| -|
|특징 | 기본 이동생성자|

||~JSONParser()|
|-| -|
|특징 | 기본 소멸자 |

</details>

### 멤버함수

<details>
<summary>펼치기/접</summary>

||BuildJSONTreeFromFile()|
|-|-|
|정의|bool BuildJSONTreeFromFile(const string& FilePath, RootNode& rootNode);|
|설명|매개변수로 받은 파일 위치에서 파일을 읽어와, 매개변수로 받은 RootNode에 JSONTree를 빌드한다. 그리고 결과 반환|
|매개변수 1|타입:const std::string&<br>읽어올 json의 경로|
|매개변수 2|타입:RootNode&<br>JSONTree가 빌드될 진입점|
|반환|타입:bool<br>true:빌드 성공<br>false:빌드 과정에서 문제 발생|
|false가 나오는 조건|1. 파일 경로에 파일이 없다.|
||2. FileIOManager의 파일 읽어오기 실패|
||2-1. ifstream이 열리지 않았다.|
||2-2. 파일이 없다.|
||3. BuildJSONTreeFromString()함수의 실패.<br>이 문단은 바로 밑에 false가 나오는 조건이 있다.|

||BuildJSONTreeFromString()|
|-|-|
|정의|bool BuildJSONTreeFromString(const string& sourceString, RootNode& rootNode);|
|설명|매개변수로 받은 문자열에서 JSONTree를 매개변수로 받은 RootNode에 빌드한다. 그리고 결과 반환|
|매개변수 1|타입:const std::string&<br>JSONTree로 빌드할 문자열|
|매개변수 2|타입:RootNode&<br>JSONTree가 빌드될 진입점|
|반환|타입:bool<br>true:빌드 성공<br>false:빌드 과정에서 문제 발생|
|false가 나오는 조건|1. 문자열이 비어있다.|
||2. Tokenizer의 토큰화 실패|
||2-1. 입력된 문자열을 토큰화 하는 과정에서, 올바르지 않은 문법이 있다는걸 감지|
||3. JSONTreeBuilder의 JSONTree 빌드 실패|
||3-1. RootNode가 비어있지 않다.|
||3-2. 토큰에 문제가 있다.(ex.괄호 짝의 오류,값 대입 오류)|
||3-3. 노드 생성에 실패했다.|

||SaveJSONTreeToFile()|
|-|-|
|정의|bool SaveJSONTreeToFile(const string& FilePath, RootNode& rootNode);|
|설명|매개변수로 받은 파일에, 매개변수로 받은 RootNode에서 JSONTree를 직렬화해 저장. 그리고 결과 반환|
|매개변수 1|타입:const std::string&<br>데이터를 저장할 json의 경로|
|매개변수 2|타입:RootNode&<br>JSONTree가의 진입점|
|반환|타입:bool<br>true:저장 성공<br>false:저장 과정에서 문제 발생|
|false가 나오는 조건|1. 파일 경로에 파일이 없다.|
||2. FileIOManager의 WriteTextToFile()함수의 실패.|
||2-1. 스트림이 열리지 않았다.|
||2-2. 파일이 없다.|
||2-3. 스트림에 오류가 발생했다.|

</details>

## 용도 및 사용

JSON을 파싱하고 JSONTree로 빌드하거나, JSON을 파일에 저장하기 위해 호출하고 선언해야하는 여러 함수와 변수들을<br>사용자가 신경쓰지 않아도 되도록 해주는것이 용도입니다.

사용은 JSONParser의 인스턴스를 생성하고, 필요한 함수를 호출하면 됩니다.

### 예시

```json
{
    "asdf": "value"
}
```

```cpp

//필요한 변수들 선언
JSONParser parser;
RootNode root;

std::cout << parser.BuildJSONTreeFromFile(".\\testingFiles\\test.json", root) << '\n';//파일에서 json데이터를 읽어와 root에 JSONTree를 빌드한다
//출력 : 1

std::cout << root["asdf"].AsString() << '\n';//출력 : 

root["asdf"] = "hello, json";//키 asdf의 값을 hello, json으로 변경

std::cout << parser.SaveJSONTreeToFile(".\\testingFiles\\test.json", root) << '\n';//JSONTree를 직렬화해 json파일에 저장
//출력 : 1

```

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)