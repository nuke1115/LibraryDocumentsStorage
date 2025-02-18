# BoolNode (class, Derived from BaseNode)

### ���:
JSON�� Value�� Bool������ Value�� �����ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/Node.hpp �� 105��° ��

### ����:
JSON�� Value�� Bool������ Value�� ǥ���ϱ� ����, BaseNodeŬ������ ��ӹ޾� ������ ����Դϴ�.

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::Bool�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||BoolNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Bool��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||BoolNode(const BoolNode&)|
|-|-|
|����|������ �Լ�|

||BoolNode(BoolNode&&)|
|-|-|
|����|������ �Լ�|

||~BoolNode()|
|-|-|
|Ư¡|����ִ�|

</details>

---

### ����Լ�

�� Ŭ������ override�� ���� ��� ����Լ��� BaseNode�κ��� ��ӹ޾� �����˴ϴ�.

<details>
<summary>��ġ��/����</summary>

||GetNodeType()|
|-|-|
|����|����� Ÿ���� ��ȯ�Ѵ�.|
|Ư¡|BaseClass�� �Լ��� �״�� ����մϴ�.|
|��ȯ|Ÿ��:UglyJSONParser::NodeType<br>����� Ÿ��|

||GetName()|
|-|-|
|����|����� �̸��� const ������ ��ȯ�Ѵ�.|
|Ư¡|BaseClass�� �Լ��� �״�� ����մϴ�.|
|��ȯ|Ÿ��:std::string<br>����� �̸��� const ����|

||GetJsonTreeByString()|
|-|-|
|����|string GetJsonTreeByString() override|
|����|BoolNode�� ������(���� boolData�� Ī��)�� bool�� (true)�� ���ڿ���(true)��,<br>bool��(false)�� ���ڿ���(false)�� ��ȯ|
|��ȯ|Ÿ��:std::string<br>std::string�� ���·� ��ȯ�� boolData|

||AsBool()|
|-|-|
|����|bool AsBool() const override;|
|����|boolData�� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:bool<br>BoolNode�� ������|

||operator=()|
|-|-|
|�����ε� 4|void operator=(const bool boolData) override|
|����|�Ű������� ���� bool�����͸� boolData�� �����մϴ�.|
|�Ű�����|Ÿ��:const bool<br>BoolNode�� ������ bool ������|


||GetChildNodeCount()|
|-|-|
|����|size_t GetChildNodeCount() const override;|
|Ư¡|�׻� 0 ��ȯ|
|��ȯ|Ÿ��:size_t<br>�ڽĳ���� ����|

||Contains()|
|-|-|
|����|bool Contains(const std::string& key) const override;|
|Ư¡|�׻� false ��ȯ|
|�Ű�����|const std::string&<br>�˻��� �̸�|
|��ȯ|Ÿ��:bool<br>true:�ִ�<br>false:����|

</details>
        

---

## Ŭ������ �뵵

BoolNode�� JSON�� BoolŸ���� Value�� ǥ���ϱ� ���� ���˴ϴ�.

����, �ٸ� Ÿ���� �������� ����� �Ǵ� ��� ����/������ �õ��� ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

## Ŭ������ ���

BoolNode�� �ܼ��� JSON�� Bool Value������ ������ BoolŸ���� �������� ��/��¸� �����մϴ�.

### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "bool1": true,
    "bool2" :  false
}
```

```cpp
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json7.json", root) << '\n';//��� : true

//Ȯ��
std::cout << "bool1 : " << root["bool1"].AsBool() << '\n';//��� :bool1 : 1

std::cout << "bool1 GetJsonTreeByString : " << root["bool1"].GetJsonTreeByString() << '\n'; //��� : bool1 GetJsonTreeByString : true

std::cout << "bool2 : " << root["bool2"].AsBool() << '\n';//��� : bool2 : 0

root["bool2"] = true;

std::cout << "bool2 : " << root["bool2"].AsBool() << '\n';//��� :bool2 : 1

std::cout << typeid(root["bool2"]).name() << '\n';//��� :class UglyJSONParser::BoolNode
```

---

## <span style="color:red">����</span>

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ����� BoolNode���� ȣ��� ��Ÿ�� ������ �߻���ŵ�ϴ�.

||����� ������ �Լ���|
|-|-|
||operator=()|
|�����ε� 1|void operator=(const string& strData) override|
|�����ε� 2|void operator=(const char* strData) override|
|�����ε� 3|void operator=(const long long intData) override|
|�����ε� 5|void operator=(const double doubleData) override|
||----------------|
|����|long long AsInt() const override;<br>const string& AsString() const override;<br>double AsDouble() const override;|
||----------------|
||operator\[\]()|
|�����ε� 1|BaseNode& operator\[\](const string& strKey) override;|
|�����ε� 2|BaseNode& operator\[\](const size_t intKey) override;|
||----------------|
||GetChildNodeVector()|
|����|std::vector<BaseNode*>& GetChildNodeVector() override;|
||----------------|
||Clear()|
|����|void Clear() override;|
||----------------|
||DeleteChildNode()|
|�����ε� 1|void DeleteChildNode(const string& strKey) override;|
|�����ε� 2|void DeleteChildNode(size_t intKey) override;|
||----------------|
||CreateNewNode()|
|�����ε� 1|bool CreateNewNode(NodeType type, string strKey) override;|
|�����ε� 2|bool CreateNewNode(NodeType type) override;|

�� �Լ����� BoolNode���� ȣ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)