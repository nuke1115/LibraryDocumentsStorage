# NodeFactory (class)

### 요약:

Node를 생성해주는 기능을 담당하는 클래스

### 정의된 파일 및 위치:

Include/UglyJSONParser/JSONTree/Node.hpp 의 13번째 줄

### 설명:

UglyJSONParser라이브러리 내부에서 Node를 생성하는 역할을 하는 클래스 입니다.

개발 초기에 Object/Array노드에서 직접 노드를 생성하는 방식으로 했지만,

추후 개발과 유지보수를 위해, 노드를 생성하는 역할을 본 클래스로 옮겼습니다.

## 멤버들:

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

||NodeFactory()|
|-|-|
|특징|기본 생성자|

||NodeFactory(const NodeFactory&)|
|-|-|
|특징|기본 복사 생성자|

||NodeFactory(NodeFactory&&)|
|-|-|
|특징|기본 이동 생성자|

||~NodeFactory()|
|-|-|
|특징|기본 소멸자|

</details>

### 멤버함수

<details>
<summary>펼치기/접기</summary>

||CreateNode()|
|-|-|
|정의|BaseNode* CreateNode(NodeType type, std::string name);|
|설명|노드의 타입과 이름을 입력받아 새로운 노드를 동적할당하여 포인터를 반환.|
|매개변수 1|UglyJSONParser::NodeType<br>생성할 노드의 타입|
|매개변수 2|std::string<br>생성할 노드의 이름|
|반환|타입:UglyJSONParser::BaseNode*<br>노드의 포인터:노드의 생성이 정상적으로 되었습니다.<br>nullptr:노드의 생성이 실패했습니다.|

</details>

## 용도 및 사용

UglyJSONParser에서 Node를 생성하는 용도로 사용되는 클래스 입니다.

클래스를 인스턴스화 해서 CreateNode() 함수에 원하는 노드의 타입과 이름을 넣어 노드를 생성하면 됩니다.

그러나, 이 클래스를 사용자가 직접 사용할 일이 없도록 라이브러리가 설계되었습니다.

따라서 다음 문단의 위험성을 감수하면서, 굳이 이 클래스를 직접 사용할 필요는 없습니다.

### 예시

```cpp
//NodeFactory 인스턴스 생성
NodeFactory factory;

BaseNode* ptr = factory.CreateNode(NodeType::Bool, "node");//노드 생성

*ptr = true;//노드에 값 대입

std::cout << ptr->AsBool();//노드에서 값 추출

delete ptr;//동적할당 해제
```

## <span style="color:red">주의</span>
만약, 해달 클래스를 통해 노드를 직접 생성하였다면,

반드시 생성한 노드를 delete 연산자를 통해 지워주십시오.

그렇지 않으면 메모리 누수가 발생합니다.

const std::list<std::string>&

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)