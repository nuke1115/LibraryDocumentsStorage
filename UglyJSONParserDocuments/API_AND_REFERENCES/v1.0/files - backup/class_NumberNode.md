# NumberNode (class, Derived from BaseNode)

### ���:
JSON�� Value�� Number������ Value�� �����ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/Node.hpp �� 61��° ��

### ����:
JSON�� Value�� Number������ Value�� ǥ���ϱ� ����, BaseNodeŬ������ ��ӹ޾� ������ ����Դϴ�.

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::Number�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

���ο� double������ �����͸� �����ϴ� ����(���� doubleData�� Ī��)��, long long ������ �����͸� �����ϴ� ����(���� intData�� Ī��)
<br>,� ������ �����ͷ� ���� ���������� �����ϴ� ����(���� isItDouble�� Ī��)�� �ִ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||NumberNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Number��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||NumberNode(const NumberNode&)|
|-|-|
|����|������ �Լ�|

||NumberNode(NumberNode&&)|
|-|-|
|����|������ �Լ�|

||~NumberNode()|
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
|����|���� isItDouble�� true�� doubleData�� ���ڿ��� ��ȯ�� ��ȯ<br>isItDouble�� false�� intData�� ���ڿ��� ��ȯ�� ��ȯ|
|��ȯ|Ÿ��:std::string<br>isItDouble�� true�϶�:���ڿ��� ��ȯ�� doubleData<br>isItDouble�� false�϶�:���ڿ��� ��ȯ�� intData|

||AsInt()|
|-|-|
|����|long long AsInt() const override;|
|����|isItDouble�� true��doubleData�� long long���� ĳ���� �ؼ�, false�� intData�� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:long long<br>NumberNode�� ������|

||AsDouble()|
|-|-|
|����|double AsDouble() const override;|
|����|isItDouble�� true��doubleData��, false�� intData�� double�� ĳ���� �ؼ� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:double<br>NumberNode�� ������|

||operator=()|
|-|-|
|�����ε� 3|void operator=(const long long intData) override|
|����|isItDouble�� false�� �ٲٰ�,<br>�Ű������� ���� �����͸� intData�� �����մϴ�.|
|<span style="color:red">����</span>|v1.0���� �� �����ε� �̿��, static_cast\<long long\>����<br>��������� Ÿ�� ������ ���ϸ�, ������ ���� �߻�.|
|�Ű�����|Ÿ��:const long long<br>NumberNode�� ������ long long ������|

||operator=()|
|-|-|
|�����ε� 5|void operator=(const double doubleData) override|
|����|isItDouble�� true�� �ٲٰ�,<br>�Ű������� ���� �����͸� doubleData�� �����մϴ�.|
|�Ű�����|Ÿ��:const double<br>NumberNode�� ������ double ������|

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
        
���� ���� �Լ� �̿��� �Լ��� �� ��忡�� ȣ��� ��Ÿ�� ������ �߻��մϴ�.

---

## Ŭ������ �뵵

NumberNode�� JSON�� NumberŸ���� Value�� ǥ���ϱ� ���� ���˴ϴ�.

����, �ٸ� Ÿ���� �������� ����� �Ǵ� ��� ����/������ �õ��� ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

## Ŭ������ ���

NumberNode�� �ܼ��� JSON�� Number Value������ ������ NumberŸ���� �������� ��/��¸� �����մϴ�.

������, �ٸ� ������� �ٸ���, NumberNode�� Number Value�� ���ϴ� ������ �Ǽ�, �ΰ��� �ڷ����� ���� �����մϴ�.

������� isItDouble�� true�϶��� �Ǽ����� ���ϴ� �����͸�, false�϶��� �������� ���ϴ� �����͸� �����մϴ�.

�����ϴ� ������ Ÿ���� ���� ���������� operator=()�� ȣ���� Ÿ�Կ� ���� �޶����ϴ�.

����, ���� ���������� ȣ���� Ÿ���� �Ǽ����̶��, isItDouble�� true��, �ƴ϶�� false�� ����˴ϴ�.

### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "double data": 3.141592,
    "long long data":20000 
}
```

```cpp
//stupid compiler and c++
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json8.json", root) << '\n';//��� : true

//Ȯ��

std::cout << "double data as double : " << root["double data"].AsDouble() << '\n';//��� : 
std::cout << "long long data as int(long long) : " << root["long long data"].AsInt() << '\n';//��� : 

std::cout << "double data as int(long long) : " << root["double data"].AsInt() << '\n';//��� : 
std::cout << "long long data as double : " << root["long long data"].AsDouble() << '\n';//��� : 
    
root["double data"] = static_cast<long long>(2025);//����Ÿ���� �����͸� �Է��Ҷ�, static_cast<long long>()���� ��������� ������ �����ָ� ������ ���� �߻�
//double => long long���� �����ϴ� ������ ��ȯ
std::cout << root["double data"].AsDouble() << '\n'; //��� : 2025

root["long long data"] = 3.1518;
//long long => double�� �����ϴ� ������ ��ȯ
std::cout << root["long long data"].AsDouble() << '\n';//��� : 3.1518
```

---

## <span style="color:red">����</span>

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ����� NumberNode���� ȣ��� ��Ÿ�� ������ �߻���ŵ�ϴ�.

||����� ������ �Լ���|
|-|-|
||operator=()|
|�����ε� 1|void operator=(const string& strData) override|
|�����ε� 2|void operator=(const char* strData) override|
|�����ε� 4|void operator=(const bool boolData) override|
||----------------|
|����|const string& AsString() const override;<br>bool AsBool() const override;|
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

�� �Լ����� NumberNode���� ȣ���, ��Ÿ�� ������ �߻���ŵ�ϴ�.

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)