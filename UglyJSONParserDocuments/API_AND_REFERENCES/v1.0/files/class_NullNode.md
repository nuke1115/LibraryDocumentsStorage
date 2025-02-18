# NullNode (class, Derived from BaseNode)

### ���:

JSON�� Value�� Null������ Value�� ǥ���ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/JSONTree/Node.hpp �� 233��° ��

### ����:

JSON�� Value�� Null������ Value�� ǥ���ϱ� ���� ������� ���

�� ���� ������ Null���� ǥ���ϱ⿡ ����ֽ��ϴ�.

�̷��� Ư¡������, ��� ��ü�� ����(�̸�,Ÿ��)�� ������ ��� ���� ���� �� ������ �Ұ��ϰ�, �ڽĳ�嵵 ���� �� �����ϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||NullNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Null�̶�� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||NullNode(const NullNode&)|
|-|-|
|����|������ �Լ�|

||NullNode(NullNode&&)|
|-|-|
|����|������ �Լ�|

||~NullNode()|
|-|-|
|Ư¡|����ִ�.|

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
|����|'\0'�� null�� �ƴ� (null) �̶�� ���ڿ��� ��ȯ.|
|��ȯ|Ÿ��:std::string<br>(null)�̶��  ���ڿ�|

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
        
���� �Լ���� ����/�Ҹ��ڵ��� ������ ��� �Լ���, �� ���(NullNode)������ ��Ÿ�� ������ �߻���ŵ�ϴ�.

---

## Ŭ������ �뵵

NullNode�� ������ null�̶�� ���� ǥ���ϱ� ���� �뵵�θ� ���˴ϴ�.

����, �����͸� �ְų� �������ų�, ��带 ������ �� �����ϴ�.

## Ŭ������ ���

NullNode�� json�� �Ľ��Ҷ� null�̶�� ������ ������ ��带 ǥ���ϱ� ���ؼ��� �����մϴ�.

��, ������ ����� ��尡 �ƴմϴ�.

### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "key" :  null
}
```


```cpp
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;


std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json5.json", root) << '\n';//��� : true
    
//Ȯ��
std::cout << root.GetJsonTreeByString() << '\n';//��� : {"key":null}

std::cout << root["key"].GetJsonTreeByString() << '\n';//��� : null

std::cout << typeid(root["key"]).name() << '\n';//��� : class UglyJSONParser::NullNode
```

---

## <span style="color:red">����</span>

null���� **JSON�� ����ִٶ�� �ǹ��� null�� ǥ���ϴ� ���**�Դϴ�.

����, **������� �õ��ҽ� ��Ÿ�� ������ �߻��մϴ�.** (��, GetNodeType(), GetName(), GetJsonTreeByString(), ������ ����)

����, Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ����� NullNode���� ȣ���ϸ� ��Ÿ�� ������ �߻��մϴ�.


||AsString()<br>AsInt()<br>AsBool()<br>AsDouble()|
|-|-|
|����|const string& AsString() const override;<br>long long AsInt() const override;<br>bool AsBool() const override;<br>double AsDouble() const override;|

||operator=()|
|-|-|
|�����ε� 1|void operator=(const string& strData) override|
|�����ε� 2|void operator=(const char* strData) override|
|�����ε� 3|void operator=(const long long intData) override|
|�����ε� 4|void operator=(const bool boolData) override|
|�����ε� 5|void operator=(const double doubleData) override|

||operator\[\]()|
|-|-|
|�����ε� 1|BaseNode& operator\[\](const string& strKey) override;|
|����|�� �����ε�� const std::string& Ÿ���� ���ڿ��� �Է¹޾�, ��ġ�ϴ� �̸��� ���� ��带 childNodeVector���� ã�� ������ ��ȯ�մϴ�.|

||operator\[\]()|
|-|-|
|�����ε� 2|BaseNode& operator\[\](const size_t intKey) override;|
  
||GetChildNodeVector()|
|-|-|
|����|std::vector<BaseNode*>& GetChildNodeVector() override;|

||Clear()|
|-|-|
|����|void Clear() override;|

||DeleteChildNode()|
|-|-|
|�����ε� 1|void DeleteChildNode(const string& strKey) override;|

||DeleteChildNode()|
|-|-|
|�����ε� 2|void DeleteChildNode(size_t intKey) override;|

||CreateNewNode()|
|-|-|
|�����ε� 1|bool CreateNewNode(NodeType type, string strKey) override;|

||CreateNewNode()|
|-|-|
|�����ε� 2|bool CreateNewNode(NodeType type) override;|

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)