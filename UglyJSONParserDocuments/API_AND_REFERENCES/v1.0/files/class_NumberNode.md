# NumberNode (class, Derived from BaseNode)

### 요약:
JSON의 Value중 Number형태의 Value를 저장하기 위해 만들어진 노드

### 정의된 파일 및 위치:
Include/UglyJSONParser/JSONTree/Node.hpp 의 61번째 줄

### 설명:
JSON의 Value중 Number형태의 Value를 표현하기 위해, BaseNode클래스를 상속받아 구현된 노드입니다.

BaseNode를 상속받았기에, BaseNode타입의 포인터나 참조로 가리킬 수 있습니다.

NodeTypes에 Nodetype::Number로 노드의 enum 코드가 정의되어있습니다.

내부에 double형태의 데이터를 저장하는 공간(이하 doubleData로 칭함)과, long long 형태의 데이터를 저장하는 공간(이하 intData로 칭함)
<br>,어떤 형태의 데이터로 현제 저장중인지 저장하는 공간(이하 isItDouble로 칭함)이 있다.

---

## 멤버들

### 생성자 및 소멸자
<details>
<summary>펼치기/접기</summary>

||NumberNode(string name)|
|-|-|
|설명|노드의 이름을 받고, 그것과 Nodetype::Number라는 enum상수값을 BaseNode 생성자에 전달해, 노드의 이름과 타입을 저장합니다.|
|매개변수|타입:std::string<br>노드의 이름|

||NumberNode(const NumberNode&)|
|-|-|
|설명|삭제된 함수|

||NumberNode(NumberNode&&)|
|-|-|
|설명|삭제된 함수|

||~NumberNode()|
|-|-|
|특징|비어있다|

</details>

---

### 멤버함수

이 클래스의 override가 붙은 모든 멤버함수는 BaseNode로부터 상속받아 구현됩니다.

<details>
<summary>펼치기/접기</summary>

||GetNodeType()|
|-|-|
|설명|노드의 타입을 반환한다.|
|특징|BaseClass의 함수를 그대로 사용합니다.|
|반환|타입:UglyJSONParser::NodeType<br>노드의 타입|

||GetName()|
|-|-|
|설명|노드의 이름을 const 참조로 반환한다.|
|특징|BaseClass의 함수를 그대로 사용합니다.|
|반환|타입:std::string<br>노드의 이름의 const 참조|

||GetJsonTreeByString()|
|-|-|
|정의|string GetJsonTreeByString() override|
|설명|만약 isItDouble이 true면 doubleData를 문자열로 변환해 반환<br>isItDouble이 false면 intData를 문자열로 변환해 반환|
|반환|타입:std::string<br>isItDouble이 true일때:문자열로 변환한 doubleData<br>isItDouble이 false일때:문자열로 변환한 intData|

||AsInt()|
|-|-|
|정의|long long AsInt() const override;|
|설명|isItDouble이 true면doubleData을 long long으로 캐스팅 해서, false면 intData를 반환합니다.|
|반환|타입:long long<br>NumberNode의 데이터|

||AsDouble()|
|-|-|
|정의|double AsDouble() const override;|
|설명|isItDouble이 true면doubleData를, false면 intData를 double로 캐스팅 해서 반환합니다.|
|반환|타입:double<br>NumberNode의 데이터|

||operator=()|
|-|-|
|오버로드 3|void operator=(const long long intData) override|
|설명|isItDouble을 false로 바꾸고,<br>매개변수로 들어온 데이터를 intData에 복사합니다.|
|<span style="color:red">주의</span>|v1.0기준 이 오버로드 이용시, static_cast\<long long\>으로<br>명시적으로 타입 지정을 안하면, 컴파일 오류 발생.|
|매개변수|타입:const long long<br>NumberNode에 저장할 long long 데이터|

||operator=()|
|-|-|
|오버로드 5|void operator=(const double doubleData) override|
|설명|isItDouble을 true로 바꾸고,<br>매개변수로 들어온 데이터를 doubleData에 복사합니다.|
|매개변수|타입:const double<br>NumberNode에 저장할 double 데이터|

||GetChildNodeCount()|
|-|-|
|정의|size_t GetChildNodeCount() const override;|
|특징|항상 0 반환|
|반환|타입:size_t<br>자식노드의 갯수|

||Contains()|
|-|-|
|정의|bool Contains(const std::string& key) const override;|
|특징|항상 false 반환|
|매개변수|const std::string&<br>검사할 이름|
|반환|타입:bool<br>true:있다<br>false:없다|

</details>
        
위에 적힌 함수 이외의 함수를 이 노드에서 호출시 런타임 오류가 발생합니다.

---

## 클래스의 용도

NumberNode는 JSON의 Number타입의 Value를 표현하기 위해 사용됩니다.

따라서, 다른 타입의 데이터의 입출력 또는 노드 생성/삭제를 시도할 경우, 런타임 에러를 발생시킵니다.

## 클래스의 사용

NumberNode는 단순히 JSON의 Number Value형식을 따르는 Number타입의 데이터의 입/출력만 가능합니다.

하지만, 다른 노드들과는 다르게, NumberNode는 Number Value에 속하는 정수와 실수, 두가지 자료형을 저장 가능합니다.

예를들어 isItDouble가 true일때는 실수형에 속하는 데이터를, false일때는 정수형에 속하는 데이터를 저장합니다.

저장하는 데이터 타입은 가장 마지막으로 operator=()를 호출한 타입에 따라서 달라집니다.

만약, 가장 마지막으로 호출한 타입이 실수형이라면, isItDouble은 true로, 아니라면 false로 저장됩니다.

### 예시

다음은 예시들입니다.

예제 json 파일:
```json
{
    "double data": 3.141592,
    "long long data":20000 
}
```

```cpp
//stupid compiler and c++
//필요한 변수들 선언
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json8.json", root) << '\n';//출력 : true

//확인

std::cout << "double data as double : " << root["double data"].AsDouble() << '\n';//출력 : 
std::cout << "long long data as int(long long) : " << root["long long data"].AsInt() << '\n';//출력 : 

std::cout << "double data as int(long long) : " << root["double data"].AsInt() << '\n';//출력 : 
std::cout << "long long data as double : " << root["long long data"].AsDouble() << '\n';//출력 : 
    
root["double data"] = static_cast<long long>(2025);//정수타입의 데이터를 입력할때, static_cast<long long>()으로 명시적으로 지정을 안해주면 컴파일 오류 발생
//double => long long으로 저장하는 데이터 변환
std::cout << root["double data"].AsDouble() << '\n'; //출력 : 2025

root["long long data"] = 3.1518;
//long long => double로 저장하는 데이터 변환
std::cout << root["long long data"].AsDouble() << '\n';//출력 : 3.1518
```

---

## <span style="color:red">주의</span>

트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

다음 함수들은 NumberNode에서 호출시 런타임 오류를 발생시킵니다.

||사용이 금지된 함수들|
|-|-|
||operator=()|
|오버로드 1|void operator=(const string& strData) override|
|오버로드 2|void operator=(const char* strData) override|
|오버로드 4|void operator=(const bool boolData) override|
||----------------|
|정의|const string& AsString() const override;<br>bool AsBool() const override;|
||----------------|
||operator\[\]()|
|오버로드 1|BaseNode& operator\[\](const string& strKey) override;|
|오버로드 2|BaseNode& operator\[\](const size_t intKey) override;|
||----------------|
||GetChildNodeVector()|
|정의|std::vector<BaseNode*>& GetChildNodeVector() override;|
||----------------|
||Clear()|
|정의|void Clear() override;|
||----------------|
||DeleteChildNode()|
|오버로드 1|void DeleteChildNode(const string& strKey) override;|
|오버로드 2|void DeleteChildNode(size_t intKey) override;|
||----------------|
||CreateNewNode()|
|오버로드 1|bool CreateNewNode(NodeType type, string strKey) override;|
|오버로드 2|bool CreateNewNode(NodeType type) override;|

위 함수들은 NumberNode에서 호출시, 런타임 오류를 발생시킵니다.

# 돌아가기

[BaseNode (Base Class)](class_BaseNode.md)