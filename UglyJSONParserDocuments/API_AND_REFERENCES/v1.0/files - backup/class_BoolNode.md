# BoolNode (class, Derived from BaseNode)

### 요약:
JSON의 Value중 Bool형태의 Value를 저장하기 위해 만들어진 노드

### 정의된 파일 및 위치:
Include/UglyJSONParser/JSONTree/Node.hpp 의 105번째 줄

### 설명:
JSON의 Value중 Bool형태의 Value를 표현하기 위해, BaseNode클래스를 상속받아 구현된 노드입니다.

BaseNode를 상속받았기에, BaseNode타입의 포인터나 참조로 가리킬 수 있습니다.

NodeTypes에 Nodetype::Bool로 노드의 enum 코드가 정의되어있습니다.

---

## 멤버들

### 생성자 및 소멸자
<details>
<summary>펼치기/접기</summary>

||BoolNode(string name)|
|-|-|
|설명|노드의 이름을 받고, 그것과 Nodetype::Bool라는 enum상수값을 BaseNode 생성자에 전달해, 노드의 이름과 타입을 저장합니다.|
|매개변수|타입:std::string<br>노드의 이름|

||BoolNode(const BoolNode&)|
|-|-|
|설명|삭제된 함수|

||BoolNode(BoolNode&&)|
|-|-|
|설명|삭제된 함수|

||~BoolNode()|
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
|설명|BoolNode의 데이터(이하 boolData로 칭함)를 bool의 (true)면 문자열의(true)로,<br>bool의(false)면 문자열의(false)로 반환|
|반환|타입:std::string<br>std::string의 형태로 변환한 boolData|

||AsBool()|
|-|-|
|정의|bool AsBool() const override;|
|설명|boolData를 반환합니다.|
|반환|타입:bool<br>BoolNode의 데이터|

||operator=()|
|-|-|
|오버로드 4|void operator=(const bool boolData) override|
|설명|매개변수로 들어온 bool데이터를 boolData에 복사합니다.|
|매개변수|타입:const bool<br>BoolNode에 저장할 bool 데이터|


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
        

---

## 클래스의 용도

BoolNode는 JSON의 Bool타입의 Value를 표현하기 위해 사용됩니다.

따라서, 다른 타입의 데이터의 입출력 또는 노드 생성/삭제를 시도할 경우, 런타임 에러를 발생시킵니다.

## 클래스의 사용

BoolNode는 단순히 JSON의 Bool Value형식을 따르는 Bool타입의 데이터의 입/출력만 가능합니다.

### 예시

다음은 예시들입니다.

예제 json 파일:
```json
{
    "bool1": true,
    "bool2" :  false
}
```

```cpp
//필요한 변수들 선언
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json7.json", root) << '\n';//출력 : true

//확인
std::cout << "bool1 : " << root["bool1"].AsBool() << '\n';//출력 :bool1 : 1

std::cout << "bool1 GetJsonTreeByString : " << root["bool1"].GetJsonTreeByString() << '\n'; //출력 : bool1 GetJsonTreeByString : true

std::cout << "bool2 : " << root["bool2"].AsBool() << '\n';//출력 : bool2 : 0

root["bool2"] = true;

std::cout << "bool2 : " << root["bool2"].AsBool() << '\n';//출력 :bool2 : 1

std::cout << typeid(root["bool2"]).name() << '\n';//출력 :class UglyJSONParser::BoolNode
```

---

## <span style="color:red">주의</span>

트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

다음 함수들은 BoolNode에서 호출시 런타임 오류를 발생시킵니다.

||사용이 금지된 함수들|
|-|-|
||operator=()|
|오버로드 1|void operator=(const string& strData) override|
|오버로드 2|void operator=(const char* strData) override|
|오버로드 3|void operator=(const long long intData) override|
|오버로드 5|void operator=(const double doubleData) override|
||----------------|
|정의|long long AsInt() const override;<br>const string& AsString() const override;<br>double AsDouble() const override;|
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

위 함수들은 BoolNode에서 호출시, 런타임 오류를 발생시킵니다.

# 돌아가기

[BaseNode (Base Class)](class_BaseNode.md)