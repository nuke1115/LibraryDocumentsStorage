# UglyJSONParser (Namespace)

### 정의:
UglyJSONParser의 모든 클래스,변수,함수들이 속해있는 네임스페이스.


### 소유중인 클래스:

<details>
<summary>펼치기/접기</summary>

[BaseNode (Base Class)](class_BaseNode.md)

요약 : JSONTree에 사용되는 Node들의 베이스 클래스

<details>
<summary><span style="color:green">BaseNode를 상속받는 클래스 목록 펼치기/접기</span></summary>

---

<span style="color:green">시작</span>
<ul>

[ArrayNode (Class, Derived from BaseNode)](class_ArrayNode.md)

요약 : JSON의 Value중 Array형태의 Value를 표현하기 위해 만들어진 노드

[BoolNode (Class, Derived from BaseNode)](class_BoolNode.md)

요약 : JSON의 Value중 Bool형태의 Value를 저장하기 위해 만들어진 노드

[NullNode (Class, Derived from BaseNode)](class_NullNode.md)

요약 : JSON의 Value중 Null형태의 Value를 표현하기 위해 만들어진 노드

[NumberNode (Class, Derived from BaseNode)](class_NumberNode.md)

요약 : JSON의 Value중 Number형태의 Value를 저장하기 위해 만들어진 노드

[ObjectNode (Class, Derived from BaseNode)](class_ObjectNode.md)

요약 : JSON의 Value중 Object형태의 Value를 표현하기 위해 만들어진 노드

[RootNode (Class, Derived from BaseNode)](class_RootNode.md)

요약 : JSONTree를 빌드할때, 진입점의 설정과 트리의 해제를 편하게 하기위해 만들어진 노드

[StringNode (Class, Derived from BaseNode)](class_StringNode.md)

요약 : JSON의 Value중 String형태의 Value를 저장하기 위해 만들어진 노드

</ul>
<span style="color:green">끝</span>

---

</details>

[FileIOManager (Class)](class_FileIOManager.md)

요약 : 텍스트 파일의 입출력을 관리해주는 클래스

[JSONParser (Class)](class_JSONParser.md)

요약 : JSON파일을 읽거나 쓰고, JSONTree를 빌드하는 일련의 과정을 편하게 사용하는것을 도와주는 클래스

[JSONTreeBuilder (Class)](class_JSONTreeBuilder.md)

요약 : JSONTree를 빌드해주는 기능이 모여있는 클래스

[NodeFactory (Class)](class_NodeFactory.md)

요약 : Node를 생성해주는 기능을 담당하는 클래스

[Tokenizer (Class)](class_Tokenizer.md)

요약 : 문자열을 토큰화해주는 기능을 담당하는 클래스

</details>

### 소유중인 열거형 타입들

<details>
<summary>펼치기/접기</summary>

[NodeType (Enum Class)](enum_class_NodeType.md)

요약 : 노드의 타입들을 정의하는 상수들의 집합

</details>

### 하위 네임스페이스

<details>
<summary>펼치기/접기</summary>

[StringUtils (Namespace)](namespace_StringUtils.md)

요약 : 문자 또는 문자열과 관련된 유틸리티 함수들이 모여있는 네임스페이스

[Tokens (Namespace)](namespace_Tokens.md)

요약 : JSON 토큰화에 필요한 상수들이 모여있는 네임스페이스

[TypeUtils (Namespace)](namespace_TypeUtils.md)

요약 : 타입과 관련된 유틸리티 함수들이 모여있는 네임스페이스

</details>

---

# 돌아가기

[API 문서로 돌아가기](../README_API_DOCUMENTS.md)