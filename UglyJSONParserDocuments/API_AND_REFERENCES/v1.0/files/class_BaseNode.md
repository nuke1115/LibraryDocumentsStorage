# BaseNode (Base Class)  

### 요약:
JSONTree에 사용되는 Node들의 베이스 클래스

### 정의된 파일 및 위치:
Include/UglyJSONParser/JSONTree/NodeBase.hpp

### 설명:
JSONTree에 사용되는 노드들의 기본적인 함수,멤버변수들과 인터페이스를 제공합니다.

이 노드를 상속받는 모든 하위 클래스는 반드시 BaseNode의 모든 순수 가상함수를 구현해야합니다.

또한 Array나 Object노드, 또는 RootNode에서 자식노드들이나 진입점 노드를 저장할때 BaseNode타입의 포인터 형태로 저장합니다.

이 노드는 단독으로 인스턴스화 될 수 없으며(순수 가상함수들 때문), 반드시 이 노드를 상속받아 구현한 하위 클래스를 가리키는 포인터나 인자의 형태로 사용되어야 합니다.

이 클래스를 상속받아 구현한 클래스(통칭 노드)들로 JSONTree를 구성합니다.

---

## 멤버들

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

||BaseNode(string name, NodeType nodeType)|
|-|-|
|설명|노드의 이름과 타입을 인자로 받아서, 노드에 저장한다.|
|매개변수 1|타입:std::string<br>노드의 이름|
|매개변수 2|타입:UglyJSONParser::NodeType<br>노드의 타입|

||BaseNode(const BaseNode&)|
|-|-|
|특징|삭제된 함수|

||BaseNode(BaseNode&&)|
|-|-|
|특징|삭제된 함수|

||virtual ~BaseNode()|
|-|-|
|특징|가상 소멸자|

</details>

---

### 멤버함수

<details>
<summary>펼치기/접기</summary>

||GetNodeType()|
|-|-|
|정의|inline NodeType GetNodeType() const|
|설명|노드의 타입을 반환한다.|
|반환|타입:UglyJSONParser::NodeType<br>노드의 타입|

||GetName()|
|-|-|
|정의|inline const string& GetName() const|
|설명|노드의 이름을 const 참조로 반환한다.|
|반환|타입:const std::string&<br>노드의 이름|

</details>

---

### 순수 가상함수

이 항목에 속하는 함수들은 순수 가상함수로, 이 클래스를 상속받는 클래스에서 **어떤형태로든, 무조건 구현해야 합니다.**

<details>
<summary>펼치기/접기</summary>

||virtual string GetJsonTreeByString() = 0|
|-|-|
|기본 의도|이 함수를 호출한 노드를 기준으로, JSONTree를 하나의 string으로 직렬화해 반환하는 함수입니다.|

||virtual const string& AsString() const = 0<br>virtual long long AsInt() const = 0<br>virtual bool AsBool() const = 0<br>virtual double AsDouble() const = 0|
|-|-|
|기본 의도|노드에서 데이터를 얻어올때 사용하는 함수들|
|주의사항|타입에 맞지 않는 노드에서 호출할경우, 런타임 에러가 발생한다.|
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||operator=()|  
|-|-|
|오버로드 1|virtual void operator=(const string& strData) = 0|
|오버로드 2|virtual void operator=(const char* strData) = 0|
|오버로드 3|virtual void operator=(const long long intData) = 0|
|오버로드 4|virtual void operator=(const bool boolData) = 0|
|오버로드 5|virtual void operator=(const double doubleData) = 0|
|기본 의도|값을 노드에 할당하는 함수들|  
|주의사항|타입에 맞지 않는 값을 할당할 경우 런타임 에러가 발생할 수 있음.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||operator\[\]()|  
|-|-|
|오버로드 1|virtual BaseNode& operator\[\](const string& strKey) = 0|
|오버로드 2|virtual BaseNode& operator\[\](const size_t intKey) = 0|
|기본 의도|각각 문자열 키와 정수 키를 사용하여 노드를 접근하는 함수들|  
|주의사항|잘못된 타입의 키를 사용하면 런타임 에러가 발생할 수 있음.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual void DeleteChildNode(const string& strKey) = 0<br>virtual void DeleteChildNode(size_t intKey) = 0|  
|-|-|  
|기본 의도|각각 문자열 키와 정수 키를 사용하여 자식 노드를 삭제하는 함수들|  
|주의사항|잘못된 타입의 키를 사용하면 런타임 에러가 발생할 수 있음.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual bool CreateNewNode(NodeType type, string strKey) = 0<br>virtual bool CreateNewNode(NodeType type) = 0|  
|-|-|  
|기본 의도|주어진 타입과 선택적으로 키를 사용하여 새로운 노드를 생성하는 함수들|  
|주의사항|object 타입의 경우 키가 겹치면 런타임 에러가 발생한다.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual size_t GetChildNodeCount() const = 0
|-|-|
|기본 의도|이 함수를 호출한 노드의 자식노드의 갯수를 얻어온다|
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual void Clear() = 0|
|-|-|
|기본 의도|이 함수를 호출한 노드의 모든 자식노드를 삭제한다|
|주의사항|array 또는 object노드가 아닐시 런타임 에러가 발생한다.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual std::vector<BaseNode*>& GetChildNodeVector() = 0|
|-|-|
|기본 의도|이 함수를 호출한 노드의 자식노드 포인터를 저장하는 벡터를 반환한다|
|주의사항|array 또는 object노드가 아닐시 런타임 에러가 발생한다.|  
||자세한 사항은 각 구현 클래스에 서술되어있다.|

||virtual bool Contains(const string& key) const = 0|
|-|-|
|기본 의도|임력으로 받은 문자열과 일치하는 이름을 가지는 노드가 childNodeVector에 있는지 검사한다|
||자세한 사항은 각 구현 클래스에 서술되어있다.|

</details>

---

### protected 멤버변수 및 using선언

<details>
<summary>펼치기/접기</summary>

||using string = std::string|
|-|-|
|설명|string타입 변수를 std없이 편하게 선언하려고 정의했다|

||string _nodeName|
|-|-|
|설명|노드의 이름을 저장한다|

||NodeType _nodeType|
|-|-|
|설명|노드의 타입을 저장한다|

</details>

-----

### 이 클래스를 상속받는 클래스들

<details>
<summary>펼치기/접기</summary>

[ArrayNode (Class, Derived from BaseNode)](class_ArrayNode.md)

[BoolNode (Class, Derived from BaseNode)](class_BoolNode.md)

[NullNode (Class, Derived from BaseNode)](class_NullNode.md)

[NumberNode (Class, Derived from BaseNode)](class_NumberNode.md)

[ObjectNode (Class, Derived from BaseNode)](class_ObjectNode.md)

[RootNode (Class, Derived from BaseNode)](class_RootNode.md)

[StringNode (Class, Derived from BaseNode)](class_StringNode.md)

</details>

---

## 클래스의 용도

이 클래스는 기본적으로 다형성을 위한 인터페이스 목적으로 작성되었습니다.

그렇기에, 이 클래스를 단독으로 인스턴스화 할 수 없고,
이 클래스를 상속받아서 구현하거나 ,이 클래스를 상속받는 클래스를 가리키는 참조나 포인터로써만 사용됩니다.

## 클래스의 사용

```cpp

//예시들

BaseNode* CreateNode(NodeType type, std::string name); //노드를 생성하고, 업캐스팅해서 반환하는 용도로 사용

class ObjectNode : public BaseNode //다형성을 하는 용도로 사용
{
private:
    std::vector<BaseNode*> _childNodeVector; //노드들을 업캐스팅하여 한곳에 저장하는 용도의 포인터로 사용
    NodeFactory _factory;
public:
    //메서드들
};

BaseNode node; // 잘못된 사용

BaseNode node2 = new ObjectNode("이름",NodeType::Object); // 올바른 사용

```

---

## <span style="color:red">주의</span>

트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)