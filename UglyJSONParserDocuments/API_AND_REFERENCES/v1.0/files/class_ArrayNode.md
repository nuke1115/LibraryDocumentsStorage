# ArrayNode (class, Derived from BaseNode)

### 요약:
JSON의 Value중 Array형태의 Value를 표현하기 위해 만들어진 노드

### 정의된 파일 및 위치:
Include/UglyJSONParser/JSONTree/Node.hpp 의 190번째 줄

### 설명:
JSON의 Value중 Array형태의 Value를 표현하기 위해, BaseNode클래스를 상속받아 구현된 노드입니다.

BaseNode를 상속받았기에, BaseNode타입의 포인터나 참조로 가리킬 수 있습니다.

NodeTypes에 Nodetype::Array로 노드의 enum 코드가 정의되어있습니다.

ObjectNode와 마찬가지로, 해당 노드에는 값에 접근하는 연산자를 사용할 시 런타임 에러가 발생합니다.

그러나, 자식노드에 접근하고 조작하는 함수는 사용 가능합니다.

내부 std::vector에 BaseNode의 포인터 형태로 자식 노드들을 저장 가능하며, 이러한 자식 노드들에는 size_t 타입의 정수를 키값으로 이용해 []로 접근 가능합니다.

만약 문자열을 키값으로 사용하려고 시도하거나, 주어진 키값이 인덱스의 범위를 넘어가면 런타임 에러가 발생합니다.

ObjectNode와 다르게, 새로운 자식노드를 생성할때 노드의 이름을 부여해주지 않아도 상관이 없습니다.

---

## 멤버들

### 생성자 및 소멸자
<details>
<summary>펼치기/접기</summary>

||ArrayNode(string name)|
|-|-|
|설명|노드의 이름을 받고, 그것과 Nodetype::Array라는 enum상수값을 BaseNode 생성자에 전달해, 노드의 이름과 타입을 저장합니다.|
|매개변수|타입:std::string<br>노드의 이름|

||ArrayNode(const ArrayNode&)|
|-|-|
|설명|삭제된 함수|

||ArrayNode(ArrayNode&&)|
|-|-|
|설명|삭제된 함수|

||~ArrayNode()|
|-|-|
|설명|소멸자가 호출되면, Clear() 함수를 호출하고,<br>자식노드가 Object나 Array타입이면 Clear()함수를 재귀적으로 호출하여<br>모든 자식노드들을 삭제합니다.|

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
|설명|함수가 호출됐을때 ostringstream (이하 buffer라고 한다)에 ([)를 입력하고, 반환 직전에 (])를 입력합니다.|
||그리고 BaseNode로 업캐스팅된 자식노드의 포인터를 저장하는 벡터(이하 childNodeVector라 칭함)를 순회하며,<br>자식노드들을 대상으로 GetJsonTreeByString() 함수를 제귀호출하여<br>그 반환값을 buffer에 입력한다.|
||만약 현제 자식노드가 childNodeVector의 마지막 원소가 아니라면, buffer에 (,)를 입력한다|
||childNodeVector순회가 끝난다면 마지막으로 buffer에 (])를 입력하고, buffer의 .str()함수를 호출하여 문자열을 반환받아 문자열을 반환합니다.|
|반환|타입:std::string<br>이 노드를 기준으로 이 노드 포함 하위 노드들이 직렬화된 문자열|

||operator\[\]()|
|-|-|
|오버로드 2|BaseNode& operator\[\](const size_t intKey) override;|
|설명|이 오버로드는 size_t 타입의 정수 인덱스를 입력받아, 내부의 childNodeVector에서 해당 인덱스의 자식노드 포인터를 리턴합니다.|
|<span style="color:red">주의</span>|만약 입력 인덱스가 childNodeVector의 크기보다 같거나 크다면 런타임 오류가 발생합니다.<br>반드시 인덱스를 확인하여 주십시오.|
|매개변수|타입:size_t<br>참조를 가져올 노드의 인덱스|
|반환|타입:UglyJSONParser::BaseNode&<br>자식노드의 참조|
  
||GetChildNodeVector()|
|-|-|
|정의|std::vector<BaseNode*>& GetChildNodeVector() override;|
|설명|childNodeVector의 참조를 반환합니다.|
|반환|타입:std::vector\<UglyJSONParser::BaseNode*\>&<br>childNodeVector의 참조|

||Clear()|
|-|-|
|정의|void Clear() override;|
|설명|이 함수를 재귀적으로 호출하며, 자신을 기준으로 모든 자식노드를 삭제합니다.|
|작동|이 함수가 호출되면, childNodeVector를 순회하며, 만약 object 또는 arrayNode라면, Clear()함수를 재귀호출하고, 아니라면 삭제합니다. |
||그리고 루프가 끝나면 childNodeVector.clear()를 호출하여 백터를 비우고 함수를 종료합니다.|
|특징|소멸시에 자동으로 호출됨|

||DeleteChildNode()|
|-|-|
|오버로드 2|void DeleteChildNode(size_t intKey) override;|
|설명|이 오버로드는 size_t 타입의 정수 인덱스를 입력받아, 내부의 childNodeVector에서 해당 인덱스의 자식노드를 삭제합니다.|
|<span style="color:red">주의</span>|만약 입력 인덱스가 childNodeVector의 최대 인덱스보다 같거나 크다면 런타임 오류가 발생합니다.<br>반드시 인덱스를 확인하여 주십시오.|
|매개변수|타입:size_t<br>삭제할 노드의 인덱스|

||CreateNewNode()|
|-|-|
|오버로드 1|bool CreateNewNode(NodeType type, string strKey) override;|
|설명|이 오버로드는 노드의 타입과 문자열로 된 노드의 이름을 입력받아, 노드의 타입만 받는 오버로드를 호출합니다.|
||ArrayNode는 자식노드를 문자열로 된 이름이 아닌, 인덱스로 구분하기에 가능한겁니다.|
|매개변수|타입:UglyJSONParser::NodeType, std::string<br>생성할 노드의 타입과 이름|
|반환|타입:bool<br>true : 자식노드 생성에 성공했습니다.<br>false : 자식노드 생성에 문제가 발생했습니다|
|false가 반환되는 조건|1. 노드의 동적할당에 실패|

||CreateNewNode()|
|-|-|
|오버로드 2|bool CreateNewNode(NodeType type) override;|
|설명|이 오버로드는 노드의 타입을 입력받아, NodeFactory에 받은 타입과 nullName이라는 문자열 이름을 넣어서 자식노드 생성을 시도합니다.<br>성공하면 childeNodeVector에 push합니다.|
|매개변수|타입:UglyJSONParser::NodeType<br>생성할 노드의 타입|
|반환|타입:bool<br>true : 자식노드 생성에 성공했습니다.<br>false : 자식노드 생성에 문제가 발생했습니다|
|false가 반환되는 조건|1. 노드의 동적할당에 실패|

||GetChildNodeCount()|
|-|-|
|정의|size_t GetChildNodeCount() const override;|
|설명|childNodeVector.size() 의 결과를 반환합니다.|
|반환|타입:size_t<br>자식노드의 갯수|

||Contains()|
|-|-|
|정의|bool Contains(const std::string& key) const override;|
|특징|항상 false만 반환합니다.|
|반환|타입:bool<br>true:있다<br>false:없다|
|매개변수|const std::string&<br>검사할 이름|

</details>
        
여기에 적힌 함수와 오버르드들 이외에는 호출시 런타임 오류가 발생합니다.

---

## 클래스의 용도

ArrayNode는 기본적으로는 ObjectNode와 같이 **한개의 노드에 여러 노드를 저장하고 접근할 때** 사용합니다.

ArrayNode는 일반적인 array자료구조와 비슷하게, 주로 **같은 종류의 자료가 여러가지 있을때** 사용합니다.

물론, 서로 다른 종류의 자료도 보관 가능하지만, 굳이 추천하지는 않는 방법입니다.

## 클래스의 사용

기본적으로 RootNode를 제외한 모든 노드들은 사용자가 직접 인스턴스화 할 필요가 없도록 라이브러리가 설계되어있습니다.

ArrayNode와 ObjectNode에서만 사용 가능한 조작은 크게 3가지가 있습니다.

### 1. 자식노드 조작(생성/삭제)
이 종류에 속하는 함수들은 CreateNewNode()와 DeleteChildNode(), Clear() 가 있습니다.

이 함수들은 자식노드를 생성하거나 삭제할때 사용하는 함수들로,<br>CreateNewNode()와 DeleteChildNode()는 JSON데이터를 읽기만 하는것이 아닌, 직접 수정해야되는 프로그램을 만들때 자주 사용할것입니다.

Clear()함수의 경우는 해당 노드가 소멸할때 자동으로 호출되기에, 일반적인 상황에서는 사용할 일이 그다지 많지는 않을겁니다.

### 2. 자식노드 접근

이 종류에 속하는 함수는 operator\[\](size_t) 함수가 있습니다.

### 3. 자식노드 저장소 접근

이 종류에 속하는 함수로는 GetChildNodeVector()와 GetChildNodeCount() 가 있습니다.

이 GetChildNodeVector()함수는 Iterator를 간접적으로 사용하기 위해 만들어진 함수입니다.

ArrayNode의 경우는 GetChildNodeCount() 함수로 for 루프를 사용하기에, 굳이 사용할 필요는 없습니다.


### 예시

다음은 예시들입니다.

예제 json 파일:
```json
{
    "arr": [
        1,
        2,
        3
    ],
    "str_arr": [
        "asdf",
        "asdf2",
        "asdf3"
    ],
    "obj_arr": [
        { "key": 1 },
        { "key": 2 },
        {"key": 3}
    ]
}
```


```cpp

//필요한 변수들 선언
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;

//json파일에서 파일을 읽어와 root노드에 JSONTree 생성
parser.BuildJSONTreeFromFile(".\\testing\\json2.json", root);

/////////////////
//자식노드 접근
std::cout << "arr 0 : " << root["arr"][0].AsInt() << '\n';//출력 : arr 0 : 1
std::cout << "str_arr 0 : " << root["str_arr"][0].AsString() << '\n';//출력 : str_arr 0 : asdf
std::cout << "obj_arr 0 key : " << root["obj_arr"][0]["key"].AsInt() << '\n';//출력 : obj_arr 0 key : 1

std::cout << "arr operator[]() return type : " << typeid(root["arr"][0]).name() << '\n';//출력 : arr operator[]() return type : class UglyJSONParser::NumberNode
/*
operator[](size_t) 오버로드는, 인덱스로 들어온 위치의 자식노드의 참조를 반환합니다. 
*/
//////////////////

/////////////////
//자식노드 조작
//1. 자식노드 생성
std::cout << root["arr"].GetJsonTreeByString() << '\n';// 자식노드 생성 이전의 ArrayNode 상태 //출력 : [1,2,3]

std::cout << root["arr"].CreateNewNode(UglyJSONParser::NodeType::Number) << '\n';//true : 성공, false : 실패 //출력 : 1

std::cout << root["arr"].GetJsonTreeByString() << '\n';// 자식노드 생성 이후의 ArrayNode 상태 //출력 : [1,2,3,0]

//2. 자식노드 삭제

std::cout << root["str_arr"].GetJsonTreeByString() << '\n';// 자식노드 생성 이전의 ArrayNode 상태 //출력 : ["asdf","asdf2","asdf3"]

root["str_arr"].DeleteChildNode(2);//2번 인덱스(3번째)의 자식노드 삭제

std::cout << root["str_arr"].GetJsonTreeByString() << '\n';// 자식노드 생성 이후의 ArrayNode 상태 //출력 : ["asdf","asdf2"]

////////////////////
    
////////////////////
//자식노드 저장소 접근

std::cout << root["obj_arr"].GetJsonTreeByString() << '\n';//출력 : [{"key":1},{"key":2},{"key":3}]
std::cout << typeid(root["obj_arr"].GetChildNodeVector()).name() << '\n';// childNodeVector //출력 : class std::vector<class UglyJSONParser::BaseNode * __ptr64,class std::allocator<class UglyJSONParser::BaseNode * __ptr64> >
std::cout << root["obj_arr"].GetChildNodeCount();// 자식노드의 갯수 //출력 : 3

```

---

## <span style="color:red">주의</span>

string 키로 접근하는것은 허용되지 않습니다. 시도하면 런타임 오류가 발생합니다.

또한, 사용하는 정수 인덱스도 0보다 작거나, childNodeVector의 크기와 같거나 크면 런타임 오류가 발생합니다.

트리 노드의 인스턴스를 다른 변수로 복사하는것은 막혀있으며, 포인터로 접근수단을 복사하는것은 권장되지 않습니다.

다음 함수들은 ArrayNode에서 호출시 런타임 오류가 발생하는 함수들 입니다.

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

||DeleteChildNode()|
|-|-|
|오버로드 1|void DeleteChildNode(const string& strKey) override;|

# 돌아가기

[BaseNode (Base Class)](class_BaseNode.md)