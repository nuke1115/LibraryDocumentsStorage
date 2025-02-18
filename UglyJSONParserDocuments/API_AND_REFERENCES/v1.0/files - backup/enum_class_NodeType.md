# NodeType (enum class)

### 요약:
노드의 타입들을 정의하는 상수들의 집합

### 정의된 파일 및 위치:
Include/UglyJSONParser/JSONTree/NodeTypes.hpp

### 설명:
JSONTree에서 사용되는 각 노드들의 타입을 정의하는 상수들의 집합입니다.

v1.0 기준으로 총 8개가 정의되어있으며, 실제로 사용자가 주로 사용하게될 타입들은 6개 입니다.

## 상수들

<details>
<summary>펼치기/접기</summary>

|타입|설명|
|-|-|
|Null|NullNode를 정의하는 상수입니다.|
|Object|ObjectNode를 정의하는 상수입니다.|
|Array|ArrayNode를 정의하는 상수입니다.|
|String|StringNode를 정의하는 상수입니다.|
|Number|NumberNode를 정의하는 상수입니다.|
|Bool|BoolNode를 정의하는 상수입니다.|
|--구분--|이 밑의 두가지 상수는, 라이브러리 내부에서 주로 사용됩니다.|
|Root|RootNode를 정의하는 상수입니다.|
|Error|TypeUtils::GetNodeTypeOfToken() 함수에서, 토큰에 해당하는 노드 타입을 찾지 못했을때 반환하는 상수입니다.|

</details>

## 용도 및 사용

이 상수들은 노드를 생성할때 타입을 지정하기 위해서, 그리고 노드의 타입을 비교하기 위해서 제작되었습니다.

사용을 원하는 타입 상수를 지정하는 방법은 (NodeType::원하는_노드_타입) 의 형식으로 지정합니다.

```cpp

//루트노드 선언
UglyJSONParser::RootNode root;

std::cout << root.CreateRootNode(UglyJSONParser::NodeType::Object) << '\n'; // Object타입의 노드를 JSONTree의 진입점으로 설정하고, 노드를 만든다.
//출력 : 1 (성공)

std::cout << (root.GetNodeType() == UglyJSONParser::NodeType::Object) << '\n';//GetNodeType으로 root의 타입을 얻어와서, NodeType::Object와 같은지 검사한다.
//출력: 1

std::cout << (root.GetNodeType() == UglyJSONParser::NodeType::Array) << '\n';//GetNodeType으로 root의 타입을 얻어와서, NodeType::Array와 같은지 검사한다.
//출력: 0

std::cout << root.CreateNewNode(UglyJSONParser::NodeType::String, "string") << '\n';//root에 이름이 string인 NodeType::String 타입의 노드를 생성한다.
//출력 : 0 (생성 성공)

std::cout << (root["string"].GetNodeType() == UglyJSONParser::NodeType::String) << '\n';//GetNodeType으로 root["string"]의 타입을 얻어와서, NodeType::String와 같은지 검사한다.
//출력: 1

```

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)