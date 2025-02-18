# NodeType (enum class)

### ���:
����� Ÿ�Ե��� �����ϴ� ������� ����

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/NodeTypes.hpp

### ����:
JSONTree���� ���Ǵ� �� ������ Ÿ���� �����ϴ� ������� �����Դϴ�.

v1.0 �������� �� 8���� ���ǵǾ�������, ������ ����ڰ� �ַ� ����ϰԵ� Ÿ�Ե��� 6�� �Դϴ�.

## �����

<details>
<summary>��ġ��/����</summary>

|Ÿ��|����|
|-|-|
|Null|NullNode�� �����ϴ� ����Դϴ�.|
|Object|ObjectNode�� �����ϴ� ����Դϴ�.|
|Array|ArrayNode�� �����ϴ� ����Դϴ�.|
|String|StringNode�� �����ϴ� ����Դϴ�.|
|Number|NumberNode�� �����ϴ� ����Դϴ�.|
|Bool|BoolNode�� �����ϴ� ����Դϴ�.|
|--����--|�� ���� �ΰ��� �����, ���̺귯�� ���ο��� �ַ� ���˴ϴ�.|
|Root|RootNode�� �����ϴ� ����Դϴ�.|
|Error|TypeUtils::GetNodeTypeOfToken() �Լ�����, ��ū�� �ش��ϴ� ��� Ÿ���� ã�� �������� ��ȯ�ϴ� ����Դϴ�.|

</details>

## �뵵 �� ���

�� ������� ��带 �����Ҷ� Ÿ���� �����ϱ� ���ؼ�, �׸��� ����� Ÿ���� ���ϱ� ���ؼ� ���۵Ǿ����ϴ�.

����� ���ϴ� Ÿ�� ����� �����ϴ� ����� (NodeType::���ϴ�_���_Ÿ��) �� �������� �����մϴ�.

```cpp

//��Ʈ��� ����
UglyJSONParser::RootNode root;

std::cout << root.CreateRootNode(UglyJSONParser::NodeType::Object) << '\n'; // ObjectŸ���� ��带 JSONTree�� ���������� �����ϰ�, ��带 �����.
//��� : 1 (����)

std::cout << (root.GetNodeType() == UglyJSONParser::NodeType::Object) << '\n';//GetNodeType���� root�� Ÿ���� ���ͼ�, NodeType::Object�� ������ �˻��Ѵ�.
//���: 1

std::cout << (root.GetNodeType() == UglyJSONParser::NodeType::Array) << '\n';//GetNodeType���� root�� Ÿ���� ���ͼ�, NodeType::Array�� ������ �˻��Ѵ�.
//���: 0

std::cout << root.CreateNewNode(UglyJSONParser::NodeType::String, "string") << '\n';//root�� �̸��� string�� NodeType::String Ÿ���� ��带 �����Ѵ�.
//��� : 0 (���� ����)

std::cout << (root["string"].GetNodeType() == UglyJSONParser::NodeType::String) << '\n';//GetNodeType���� root["string"]�� Ÿ���� ���ͼ�, NodeType::String�� ������ �˻��Ѵ�.
//���: 1

```

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)