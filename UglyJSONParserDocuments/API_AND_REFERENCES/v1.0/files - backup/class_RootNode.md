# RootNode (class, Derived from BaseNode)

### 요약:

JSONTree를 빌드할때, 진입점의 설정과 트리의 해제를 편하게 하기위해 만들어진 노드

### 정의된 파일 및 위치:

Include/UglyJSONParser/JSONTree/Node.hpp 의 276번째 줄

### 설명:

BaseNode를 상속받았기에, BaseNode타입의 포인터나 참조로 가리킬 수 있습니다.

NodeTypes에 Nodetype::Root로 노드의 enum 코드가 정의되어있습니다.

RootNode는 다른 노드들과는 다르게 단독으로 사용될시 런타입 오류가 발생하며, 반드시 JSONTree의 진입점의 인터페이스 형태로 사용되어야 합니다.

이런 특징으로 인해, 예외적으로 사용자가 직접 인스턴스화를 해야되며, RootNode에만 CreateRootNode() 라는 함수가 제공됩니다.

---

## 멤버들

### 생성자 및 소멸자
<details>
<summary>펼치기/접기</summary>

||RootNode(string name)|
|-|-|
|설명|노드의 이름을 받고, 그것과 Nodetype::Root라는 enum상수값을 BaseNode 생성자에 전달해, 노드의 이름과 타입을 저장합니다.|
|매개변수|타입:std::string<br>노드의 이름|

||RootNode(const RootNode&)|
|-|-|
|설명|삭제된 함수|

||RootNode(RootNode&&)|
|-|-|
|설명|삭제된 함수|

||~RootNode()|
|-|-|
|설명|소멸자가 호출되면, 진입점으로 설정된 BaseNode포인터(이하 entryPoint라 칭함)가 nullptr인지 확인한다.|
||entryPoint가 nullptr가 아니라면, 노드의 타입이 Object나 Array인지 검사하고, Clear()함수를 호출한다.|
||Clear()까지 호출이 완료되면, entryPoint가 nullptr가 아닐때의 공통작업인 entryPoint를 delete해준다.|

</details>

---

### 멤버함수

이 클래스의 override가 붙은 모든 멤버함수는 BaseNode로부터 상속받아 구현됩니다.

<details>
<summary>펼치기/접기</summary>

||CreateRootNode()|
|-|-|
|정의|bool CreateRootNode(NodeType nodeType)|
|설명|NodeType타입의 노드의 타입을 받고 검사한다.|
||그리고, 받은 타입과, 클래스 내부에 저장되어있는 entryPoint용 이름으로 NodeFactory에 노드 생성을 시도한다.|
||생성된 노드가 nullptr면false를 반환하고, 아니라면 entryPoint와 RootNode의 타입을 설정하고 true 반환.|
|매개변수|UglyJSONParser::NodeType<br>노드의 타입|
|반환|타입:bool<br>true:생성 성공<br>false:생성에 문제 발생|
|false반환 조건|인자로 받은 타입이 Root또는 Error거나,<br>RootNode의 타입이 Root가 아니거나, entryPoint가 nullptr가 아니거나<br>,생성된 노드가 nullptr라면 false 반환|

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
|설명|entryPoint에 접근하여 GetJsonTreeByString() 함수 호출 후, 반환값 반환|
|반환|타입:std::string<br>entryPoint를 기준으로 이 노드 포함 하위 노드들이 직렬화된 문자열|
|<span style="color:red">주의</span>|이 함수들은 entryPoint가 nullptr면 런타입 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||AsString()<br>AsInt()<br>AsBool()<br>AsDouble()|
|-|-|
|정의|const string& AsString() const override;<br>long long AsInt() const override;<br>bool AsBool() const override;<br>double AsDouble() const override;|
|설명|entryPoint에 접근하여 함수를 호출 후, 반환값을 반환한다.|
|<span style="color:red">주의</span>|이 함수들은 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||operator=()|
|-|-|
|오버로드 1|void operator=(const string& strData) override|
|오버로드 2|void operator=(const char* strData) override|
|오버로드 3|void operator=(const long long intData) override|
|오버로드 4|void operator=(const bool boolData) override|
|오버로드 5|void operator=(const double doubleData) override|
|설명|entryPoint로 접근해 값을 대입한다.|
|<span style="color:red">주의</span>|이 함수들은 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||operator\[\]()|
|-|-|
|오버로드 1|BaseNode& operator\[\](const string& strKey) override;|
|오버로드 1 매개변수|const std::string&<br>가져올 노드의 이름|
|오버로드 2|BaseNode& operator\[\](const size_t intKey) override;|
|오버로드 2 매개변수|size_t<br>가져올 노드의 인덱스|
|설명|이 오버로드들은 const std::string& 타입의 문자열 또는 size_t 인덱스를 입력받아,<br>entryPoint에 접근하여 operator\[\]()호출 후, 반환값을 반환합니다.|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||GetChildNodeVector()|
|-|-|
|정의|std::vector<BaseNode*>& GetChildNodeVector() override;|
|설명|entryPoint에 접근해 GetChildNodeVector()호출 후, 반환값을 반환합니다.|
|반환|타입:std::vector\<UglyJSONParser::BaseNode*\>&<br>childNodeVector의 참조|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||Clear()|
|-|-|
|정의|void Clear() override;|
|설명|이 함수가 호출되면, entryPoint에 접근해 Clear() 함수를 호출합니다.|
|특징|소멸시에 entryPoint에 따라서 자동으로 호출됨|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|

||DeleteChildNode()|
|-|-|
|오버로드 1|void DeleteChildNode(const string& strKey) override;|
|오버로드 1 매개변수|타입:const std::string<br>삭제할 노드의 이름|
|오버로드 2|void DeleteChildNode(size_t intKey) override;|
|오버로드 2 매개변수|타입:size_t<br>삭제할 노드의 인덱스|
|설명|이 오버로드들은 size_t 타입의 인덱스 또는 const std::string& 타입의 이름을를 입력받아,<br>entryPoint에 접근해서 DeleteChildNode()를 호출합니다.|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|


||CreateNewNode()|
|-|-|
|오버로드 1|bool CreateNewNode(NodeType type, string strKey) override;|
|오버로드 1 매개변수|타입:UglyJSONParser::NodeType, std::string<br>생성할 노드의 타입과 이름|
|오버로드 2|bool CreateNewNode(NodeType type) override;|
|매개변수|타입:UglyJSONParser::NodeType<br>생성할 노드의 타입|
|설명|이 오버로드들은 NodeType타입의 노드의 타입 또는 타입과 할께 이름을 입력받아 entryPoint에 접근하여 CreateNewNode()를 호출하고, 반환값을 반환합니다.|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|
|공통적인 반환|타입:bool<br>true : 자식노드 생성에 성공했습니다.<br>false : 자식노드 생성에 문제가 발생했습니다|

||GetChildNodeCount()|
|-|-|
|정의|size_t GetChildNodeCount() const override;|
|설명|entryPoint에 접근해 GetChildNodeCount()를 호출하고, 반환값을 반환합니다.|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|
|반환|타입:size_t<br>자식노드의 갯수|

||Contains()|
|-|-|
|정의|bool Contains(const std::string& key) const override;|
|설명|const std::string&타입의 키를 입력받아 entryPoint에 접근해 Contains()를 호출하고, 반환값을 반환합니다.|
|<span style="color:red">주의</span>|이 함수는 entryPoint에 따라서 런타임 오류가 발생합니다.<br>호출 전에 entryPoint를 확인해 주십시오.|
|매개변수|const std::string&<br>검사할 이름|
|반환|타입:bool<br>true:있다<br>false:없다|

</details>
        

---

## 클래스의 용도

RootNode는 메모리 관리와 JSONTree에서의 일관된 진입점이 필요해서 만들어졌습니다.

몇가지의 예시를 들어봅시다.

```
1. 만약 JSONTreeBuilder에서 노드의 진입점을 동적할당해서, 그 포인터를 넘겨주었다고 생각해봅시다. 
    그런데, 만약 프로그래머가 받은 자원의 해제를 잊었다면 어떻게 될까요?

2. 만약, 트리 a,b,c가 있고, 해당 트리들의 루트노드의 타입이 다 다르다면 어떻게 할건가요?
```

RootNode는 위의 상황들을 대처하기 위해 만들어졌습니다.

RootNode는 외부에서 진입점을 생성하거나 넣는 함수 없이, 내부에 노드의 진입점을 동적할당 및 해제하는 함수를 모두 구비하고, RootNode라는 공통된 JSONTree진입점을 만듬으로써
<br> 위의 두 문제들을 대처하였습니다.
    
따라서, 유저는 RootNode로 JSONTree에 접근해서 JSON을 사용하기만 하면 됩니다.

RootNode는 JSONTree의 루트노드의 인터페이스 역할만을 하기에, RootNode로 트리에 접근한다는 곧 JSONTree의 루트노드에 접근한다와 같습니다.

## 클래스의 사용

기본적으로 사용자는 RootNode와 관련된 설정은 라이브러리가 해주기에,<br>사용자는 JSONTree에 접근하는것 말고는 RootNode를 직접 관리해야하는 경우는 밑의 2개를 제외하면 거의 없습니다.

사용자가 RootNode를 직접 관리해야하는 상황은 크게 2가지입니다.

### 1. 인스턴스화
라이브러리에서 RootNode에 JSONTree를 빌드하기 위해서, 기본적으로 RootNode의 인스턴스가 필요합니다.

이런 이유때문에, RootNode의 인스턴스를 생성하고, JSONTreeBuilder에 인스턴스를 넘기는 작업까지는 사용자가 해야합니다.

### 2. 메모리 해제(RootNode를 동적할당 헀을경우만)
스택에 할당한 경우는, 스택이 없어지면 자동으로 소멸자가 호출되지만, 힙에 동적할당된 경우는 그렇지 않습니다.

만약 RootNode 자체를 동적할당했다면, 동적할당한 리소스를 해제하는 작업은 사용자가 해야합니다.

RootNode가 해제하는 메모리는 JSONTree만입니다.

본 라이브러리는 쓰레기를 대신 수집해주지 않습니다.

### 예시

다음은 예시들입니다.

예제 json 파일:
```json
{
    "key": "value"
}
```


```cpp
//필요한 변수들 선언
UglyJSONParser::JSONParser parser;

//RootNode를 스택영역에 생성
UglyJSONParser::RootNode root;

//진입점 생성 이전의 RootNode의 타입
std::cout << static_cast<int>(root.GetNodeType()) << '\n';//출력 Root(code : 6)

std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json4.json", root) << '\n';//RootNode를 파서(내부에서 JSONTreeBuilder에 입력)에 참조로 넘긴다.
//그리고 내부에서는 root노드에 JSONTree의 진입점 역할을 할 노드를 동적할당하는 함수를 호출한다.
//출력: 성공(true)

//진입점 생성 이후의 RootNode의 타입
std::cout << static_cast<int>(root.GetNodeType()) << '\n';//출력 Object(code : 1)

////////////
//RootNode는 진입점 노드의 인터페이스 역할을 한다.
std::cout << "object key : " << root["key"].AsString() << '\n';//출력:object key : value

root.DeleteChildNode("key");

std::cout << root.GetJsonTreeByString(); // 출력:{}

///////////

//스택이 없어지면, RootNode의 소멸자가 자동으로 호출되어, 진입점을 포함한 JSONTree가 동적할당이 해제된다.
```

---

## <span style="color:red">주의</span>

RootNode의 진입점을 추출하는 함수는 없습니다.

또한, 트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

RootNode는 기본적으로 진입점이 nullptr이기에, 단독으로 사용할시 nullptr참조로 런타임 오류가 발생합니다.

# 돌아가기

[BaseNode (Base Class)](class_BaseNode.md)