# JSONTreeBuilder (class)

### 요약:

JSONTree를 빌드해주는 기능이 모여있는 클래스

### 정의된 파일 및 위치:

Include/UglyJSONParser/JSONTree/JSONTreeBuilder.hpp

### 설명:

JSONTree를 빌드하기 위해 만들어진 클래스.

JSONTree를 빌드하기 위해 내부에 여러 함수들이 선언되어있습니다.

그리고 그 함수들을 BuildJSONTree()에서 호출하며 JSONTree를 빌드합니다.

## 멤버들:

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

||JSONTreeBuilder()|
|-|-|
|특징|기본 생성자|

||JSONTreeBuilder(const JSONTreeBuilder&)|
|-|-|
|특징|기본 복사생성자|

||JSONTreeBuilder(JSONTreeBuilder&&)|
|-|-|
|특징|기본 이동생성자|

||~JSONTreeBuilder()|
|-|-|
|특징|기본 소멸자|

</details>

### 멤버함수

<details>
<summary>펼치기/접기</summary>

||BuildJSONTree()|
|-|-|
|정의|bool BuildJSONTree(RootNode& rootNode, const std::list<std::string>& tokens);|
|설명|매개변수로 받은 루트노드에, 매개변수로 받은 토큰들로 JSONTree를 빌드합니다. 그리고 결과 반환|
|매개변수 1|타입:UglyJSONparser::RootNode&<br>JSONTree가 빌드될 진입점|
|매개변수 2|const std::list<std::string>&<br>토큰들|
|반환|bool<br>true:JSONTree빌드에 성공했습니다.<br>false:JSONTree빌드 과정에 문제가 생겼습니다.|
|false가 뜨는 경우|1.RootNode가 비어있지 않다.|
||2.토큰에 문제가 있다.(ex.괄호 짝의 오류,값 대입 오류)|
||3.노드 생성에 실패했다.|

</details>

## 용도 및 사용

토큰화된 문자들을 받아 RootNode에 JSONTree를 빌드해주는 역할을 합니다.

이 클래스는 UglyJSONParser내부에서 사용됩니다.

또한, 이 클래스는 Tokenizer에서 생성된 토큰을 사용한다는 전제 하에 작성되었고,<br>이 클래스를 직접 사용할 일이 없도록 JSONParser 클래스를 만들어두었습니다.

따라서, 사용자가 이 클래스를 직접 사용할 상황은 거의 없습니다.

### 예시

```json
{
    "asdf": "value"
}
```

```cpp
//필요한 변수들 선언
FileIOManager mgr;
JSONTreeBuilder builder;
Tokenizer tokenizer;
RootNode root;
std::string str;
std::list<std::string> tokens;

mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json");//json파일을 로드한다.

tokenizer.Tokenize(str, tokens);//문자열을 토큰화한다.
    
std::cout << builder.BuildJSONTree(root, tokens) << '\n';//토큰들을 이용해 root에 JSONTree 생성
//출력 : 1

std::cout << root.GetJsonTreeByString() << '\n';// 출력 : {"asdf":"value"}
std::cout << root["asdf"].AsString() << '\n';//출력 : value
```

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)