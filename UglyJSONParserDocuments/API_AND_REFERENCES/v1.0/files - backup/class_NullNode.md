# NullNode (class, Derived from BaseNode)

### 요약:

JSON의 Value중 Null형태의 Value를 표현하기 위해 만들어진 노드

### 정의된 파일 및 위치:

Include/UglyJSONParser/JSONTree/Node.hpp 의 233번째 줄

### 설명:

JSON의 Value중 Null형태의 Value를 표현하기 위해 만들어진 노드

이 노드는 오로지 Null만을 표현하기에 비어있습니다.

이러한 특징때문에, 노드 자체의 정보(이름,타입)를 제외한 어떠한 값도 추출 및 대입이 불가하고, 자식노드도 가질 수 없습니다.

---

## 멤버들

### 생성자 및 소멸자
<details>
<summary>펼치기/접기</summary>

||NullNode(string name)|
|-|-|
|설명|노드의 이름을 받고, 그것과 Nodetype::Null이라는 enum상수값을 BaseNode 생성자에 전달해, 노드의 이름과 타입을 저장합니다.|
|매개변수|타입:std::string<br>노드의 이름|

||NullNode(const NullNode&)|
|-|-|
|설명|삭제된 함수|

||NullNode(NullNode&&)|
|-|-|
|설명|삭제된 함수|

||~NullNode()|
|-|-|
|특징|비어있다.|

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
|설명|'\0'의 null이 아닌 (null) 이라는 문자열을 반환.|
|반환|타입:std::string<br>(null)이라는  문자열|

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
        
위의 함수들과 생성/소멸자들을 제외한 모든 함수는, 이 노드(NullNode)에서는 런타임 에러를 발생시킵니다.

---

## 클래스의 용도

NullNode는 오로지 null이라는 것을 표현하기 위한 용도로만 사용됩니다.

따라서, 데이터를 넣거나 가져오거나, 노드를 생성할 수 없습니다.

## 클래스의 사용

NullNode는 json을 파싱할때 null이라는 정보를 가지는 노드를 표현하기 위해서만 존제합니다.

즉, 데이터 저장용 노드가 아닙니다.

### 예시

다음은 예시들입니다.

예제 json 파일:
```json
{
    "key" :  null
}
```


```cpp
//필요한 변수들 선언
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json5.json", root) << '\n';//출력 : true
    
//확인
std::cout << root.GetJsonTreeByString() << '\n';//출력 : {"key":null}

std::cout << root["key"].GetJsonTreeByString() << '\n';//출력 : null

std::cout << typeid(root["key"]).name() << '\n';//출력 : class UglyJSONParser::NullNode
```

---

## <span style="color:red">주의</span>

null노드는 **JSON의 비어있다라는 의미의 null을 표현하는 노드**입니다.

따라서, **입출력을 시도할시 런타임 에러가 발생합니다.** (단, GetNodeType(), GetName(), GetJsonTreeByString(), 생성자 제외)

또한, 트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

다음 함수들을 NullNode에서 호출하면 런타임 오류가 발생합니다.


||AsString()<br>AsInt()<br>AsBool()<br>AsDouble()|
|-|-|
|정의|const string& AsString() const override;<br>long long AsInt() const override;<br>bool AsBool() const override;<br>double AsDouble() const override;|

||operator=()|
|-|-|
|오버로드 1|void operator=(const string& strData) override|
|오버로드 2|void operator=(const char* strData) override|
|오버로드 3|void operator=(const long long intData) override|
|오버로드 4|void operator=(const bool boolData) override|
|오버로드 5|void operator=(const double doubleData) override|

||operator\[\]()|
|-|-|
|오버로드 1|BaseNode& operator\[\](const string& strKey) override;|
|설명|이 오버로드는 const std::string& 타입의 문자열을 입력받아, 일치하는 이름을 가진 노드를 childNodeVector에서 찾아 참조를 반환합니다.|

||operator\[\]()|
|-|-|
|오버로드 2|BaseNode& operator\[\](const size_t intKey) override;|
  
||GetChildNodeVector()|
|-|-|
|정의|std::vector<BaseNode*>& GetChildNodeVector() override;|

||Clear()|
|-|-|
|정의|void Clear() override;|

||DeleteChildNode()|
|-|-|
|오버로드 1|void DeleteChildNode(const string& strKey) override;|

||DeleteChildNode()|
|-|-|
|오버로드 2|void DeleteChildNode(size_t intKey) override;|

||CreateNewNode()|
|-|-|
|오버로드 1|bool CreateNewNode(NodeType type, string strKey) override;|

||CreateNewNode()|
|-|-|
|오버로드 2|bool CreateNewNode(NodeType type) override;|

# 돌아가기

[BaseNode (Base Class)](class_BaseNode.md)