# NodeFactory (class)

### ���:

Node�� �������ִ� ����� ����ϴ� Ŭ����

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/JSONTree/Node.hpp �� 13��° ��

### ����:

UglyJSONParser���̺귯�� ���ο��� Node�� �����ϴ� ������ �ϴ� Ŭ���� �Դϴ�.

���� �ʱ⿡ Object/Array��忡�� ���� ��带 �����ϴ� ������� ������,

���� ���߰� ���������� ����, ��带 �����ϴ� ������ �� Ŭ������ �Ű���ϴ�.

## �����:

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

||NodeFactory()|
|-|-|
|Ư¡|�⺻ ������|

||NodeFactory(const NodeFactory&)|
|-|-|
|Ư¡|�⺻ ���� ������|

||NodeFactory(NodeFactory&&)|
|-|-|
|Ư¡|�⺻ �̵� ������|

||~NodeFactory()|
|-|-|
|Ư¡|�⺻ �Ҹ���|

</details>

### ����Լ�

<details>
<summary>��ġ��/����</summary>

||CreateNode()|
|-|-|
|����|BaseNode* CreateNode(NodeType type, std::string name);|
|����|����� Ÿ�԰� �̸��� �Է¹޾� ���ο� ��带 �����Ҵ��Ͽ� �����͸� ��ȯ.|
|�Ű����� 1|UglyJSONParser::NodeType<br>������ ����� Ÿ��|
|�Ű����� 2|std::string<br>������ ����� �̸�|
|��ȯ|Ÿ��:UglyJSONParser::BaseNode*<br>����� ������:����� ������ ���������� �Ǿ����ϴ�.<br>nullptr:����� ������ �����߽��ϴ�.|

</details>

## �뵵 �� ���

UglyJSONParser���� Node�� �����ϴ� �뵵�� ���Ǵ� Ŭ���� �Դϴ�.

Ŭ������ �ν��Ͻ�ȭ �ؼ� CreateNode() �Լ��� ���ϴ� ����� Ÿ�԰� �̸��� �־� ��带 �����ϸ� �˴ϴ�.

�׷���, �� Ŭ������ ����ڰ� ���� ����� ���� ������ ���̺귯���� ����Ǿ����ϴ�.

���� ���� ������ ���輺�� �����ϸ鼭, ���� �� Ŭ������ ���� ����� �ʿ�� �����ϴ�.

### ����

```cpp
//NodeFactory �ν��Ͻ� ����
NodeFactory factory;

BaseNode* ptr = factory.CreateNode(NodeType::Bool, "node");//��� ����

*ptr = true;//��忡 �� ����

std::cout << ptr->AsBool();//��忡�� �� ����

delete ptr;//�����Ҵ� ����
```

## <span style="color:red">����</span>
����, �ش� Ŭ������ ���� ��带 ���� �����Ͽ��ٸ�,

�ݵ�� ������ ��带 delete �����ڸ� ���� �����ֽʽÿ�.

�׷��� ������ �޸� ������ �߻��մϴ�.

const std::list<std::string>&

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)