# StringNode (class, Derived from BaseNode)

### ���:
JSON�� Value�� String������ Value�� �����ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/Node.hpp �� 19��° ��

### ����:
JSON�� Value�� String������ Value�� ǥ���ϱ� ����, BaseNodeŬ������ ��ӹ޾� ������ ����Դϴ�.

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::String�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||StringNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::String��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||StringNode(const StringNode&)|
|-|-|
|����|������ �Լ�|

||StringNode(StringNode&&)|
|-|-|
|����|������ �Լ�|

||~StringNode()|
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
|����|StringNode�� ������(���� strData�� Ī��)�� (")�� ���μ� ��ȯ�Ѵ�.|
|��ȯ|Ÿ��:std::string<br>(")�� ������ strData|

||AsString()|
|-|-|
|����|const string& AsString() const override;|
|����|strData�� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:const std::string&<br>StringNode�� ������|

||operator=()|
|-|-|
|�����ε� 1|void operator=(const string& strData) override|
|�����ε� 2|void operator=(const char* strData) override|
|����|�Ű������� ���� ���ڿ� �����͸� strData�� �����մϴ�.|
|�Ű�����|Ÿ��:const std::string&<br>const char*<br>StringNode�� ������ ���ڿ� ������|


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

���� ������ �Լ��� �̿��� �Լ��� StringNode���� ����� ��Ÿ�� ���� �߻�
        

---

## Ŭ������ �뵵

StringNode�� JSON�� StringŸ���� Value�� ǥ���ϱ� ���� ���˴ϴ�.

����, �ٸ� Ÿ���� �������� ����� �Ǵ� ��� ����/������ �õ��� ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

## Ŭ������ ���

StringNode�� �ܼ��� JSON�� String Value������ ������ StringŸ���� �������� ��/��¸� �����մϴ�.

### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "str1": "value",
    "str2" :  "funky"
}
```

```cpp
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json6.json", root) << '\n';//��� : true

//Ȯ��
std::cout << "str1 : " << root["str1"].AsString() << '\n';//��� : str1 : value

std::cout << "str1 GetJsonTreeByString : " << root["str1"].GetJsonTreeByString() << '\n'; //��� : str1 GetJsonTreeByString : "value"

std::cout << "str2 : " << root["str2"].AsString() << '\n';//��� : str2 : funky

root["str2"] = "this is operator=(const char*) function test";

std::cout << "str2 : " << root["str2"].AsString() << '\n';//��� : str2 : this is operator=(const char*) function test

std::cout << typeid(root["str1"]).name() << '\n';//��� : class UglyJSONParser::StringNode
```

---

## <span style="color:red">����</span>

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ����� StringNode���� ȣ��� ��Ÿ�� ������ �߻���ŵ�ϴ�.

||����� ������ �Լ���|
|-|-|
||operator=()|
|�����ε� 3|void operator=(const long long intData) override|
|�����ε� 4|void operator=(const bool boolData) override|
|�����ε� 5|void operator=(const double doubleData) override|
||----------------|
|����|long long AsInt() const override;<br>bool AsBool() const override;<br>double AsDouble() const override;|
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

�� �Լ����� StringNode���� ȣ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)