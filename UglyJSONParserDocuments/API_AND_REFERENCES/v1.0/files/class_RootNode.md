# RootNode (class, Derived from BaseNode)

### ���:

JSONTree�� �����Ҷ�, �������� ������ Ʈ���� ������ ���ϰ� �ϱ����� ������� ���

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/JSONTree/Node.hpp �� 276��° ��

### ����:

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::Root�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

RootNode�� �ٸ� ������� �ٸ��� �ܵ����� ���ɽ� ��Ÿ�� ������ �߻��ϸ�, �ݵ�� JSONTree�� �������� �������̽� ���·� ���Ǿ�� �մϴ�.

�̷� Ư¡���� ����, ���������� ����ڰ� ���� �ν��Ͻ�ȭ�� �ؾߵǸ�, RootNode���� CreateRootNode() ��� �Լ��� �����˴ϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||RootNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Root��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||RootNode(const RootNode&)|
|-|-|
|����|������ �Լ�|

||RootNode(RootNode&&)|
|-|-|
|����|������ �Լ�|

||~RootNode()|
|-|-|
|����|�Ҹ��ڰ� ȣ��Ǹ�, ���������� ������ BaseNode������(���� entryPoint�� Ī��)�� nullptr���� Ȯ���Ѵ�.|
||entryPoint�� nullptr�� �ƴ϶��, ����� Ÿ���� Object�� Array���� �˻��ϰ�, Clear()�Լ��� ȣ���Ѵ�.|
||Clear()���� ȣ���� �Ϸ�Ǹ�, entryPoint�� nullptr�� �ƴҶ��� �����۾��� entryPoint�� delete���ش�.|

</details>

---

### ����Լ�

�� Ŭ������ override�� ���� ��� ����Լ��� BaseNode�κ��� ��ӹ޾� �����˴ϴ�.

<details>
<summary>��ġ��/����</summary>

||CreateRootNode()|
|-|-|
|����|bool CreateRootNode(NodeType nodeType)|
|����|NodeTypeŸ���� ����� Ÿ���� �ް� �˻��Ѵ�.|
||�׸���, ���� Ÿ�԰�, Ŭ���� ���ο� ����Ǿ��ִ� entryPoint�� �̸����� NodeFactory�� ��� ������ �õ��Ѵ�.|
||������ ��尡 nullptr��false�� ��ȯ�ϰ�, �ƴ϶�� entryPoint�� RootNode�� Ÿ���� �����ϰ� true ��ȯ.|
|�Ű�����|UglyJSONParser::NodeType<br>����� Ÿ��|
|��ȯ|Ÿ��:bool<br>true:���� ����<br>false:������ ���� �߻�|
|false��ȯ ����|���ڷ� ���� Ÿ���� Root�Ǵ� Error�ų�,<br>RootNode�� Ÿ���� Root�� �ƴϰų�, entryPoint�� nullptr�� �ƴϰų�<br>,������ ��尡 nullptr��� false ��ȯ|

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
|����|entryPoint�� �����Ͽ� GetJsonTreeByString() �Լ� ȣ�� ��, ��ȯ�� ��ȯ|
|��ȯ|Ÿ��:std::string<br>entryPoint�� �������� �� ��� ���� ���� ������ ����ȭ�� ���ڿ�|
|<span style="color:red">����</span>|�� �Լ����� entryPoint�� nullptr�� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||AsString()<br>AsInt()<br>AsBool()<br>AsDouble()|
|-|-|
|����|const string& AsString() const override;<br>long long AsInt() const override;<br>bool AsBool() const override;<br>double AsDouble() const override;|
|����|entryPoint�� �����Ͽ� �Լ��� ȣ�� ��, ��ȯ���� ��ȯ�Ѵ�.|
|<span style="color:red">����</span>|�� �Լ����� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||operator=()|
|-|-|
|�����ε� 1|void operator=(const string& strData) override|
|�����ε� 2|void operator=(const char* strData) override|
|�����ε� 3|void operator=(const long long intData) override|
|�����ε� 4|void operator=(const bool boolData) override|
|�����ε� 5|void operator=(const double doubleData) override|
|����|entryPoint�� ������ ���� �����Ѵ�.|
|<span style="color:red">����</span>|�� �Լ����� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||operator\[\]()|
|-|-|
|�����ε� 1|BaseNode& operator\[\](const string& strKey) override;|
|�����ε� 1 �Ű�����|const std::string&<br>������ ����� �̸�|
|�����ε� 2|BaseNode& operator\[\](const size_t intKey) override;|
|�����ε� 2 �Ű�����|size_t<br>������ ����� �ε���|
|����|�� �����ε���� const std::string& Ÿ���� ���ڿ� �Ǵ� size_t �ε����� �Է¹޾�,<br>entryPoint�� �����Ͽ� operator\[\]()ȣ�� ��, ��ȯ���� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||GetChildNodeVector()|
|-|-|
|����|std::vector<BaseNode*>& GetChildNodeVector() override;|
|����|entryPoint�� ������ GetChildNodeVector()ȣ�� ��, ��ȯ���� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:std::vector\<UglyJSONParser::BaseNode*\>&<br>childNodeVector�� ����|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||Clear()|
|-|-|
|����|void Clear() override;|
|����|�� �Լ��� ȣ��Ǹ�, entryPoint�� ������ Clear() �Լ��� ȣ���մϴ�.|
|Ư¡|�Ҹ�ÿ� entryPoint�� ���� �ڵ����� ȣ���|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|

||DeleteChildNode()|
|-|-|
|�����ε� 1|void DeleteChildNode(const string& strKey) override;|
|�����ε� 1 �Ű�����|Ÿ��:const std::string<br>������ ����� �̸�|
|�����ε� 2|void DeleteChildNode(size_t intKey) override;|
|�����ε� 2 �Ű�����|Ÿ��:size_t<br>������ ����� �ε���|
|����|�� �����ε���� size_t Ÿ���� �ε��� �Ǵ� const std::string& Ÿ���� �̸����� �Է¹޾�,<br>entryPoint�� �����ؼ� DeleteChildNode()�� ȣ���մϴ�.|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|


||CreateNewNode()|
|-|-|
|�����ε� 1|bool CreateNewNode(NodeType type, string strKey) override;|
|�����ε� 1 �Ű�����|Ÿ��:UglyJSONParser::NodeType, std::string<br>������ ����� Ÿ�԰� �̸�|
|�����ε� 2|bool CreateNewNode(NodeType type) override;|
|�Ű�����|Ÿ��:UglyJSONParser::NodeType<br>������ ����� Ÿ��|
|����|�� �����ε���� NodeTypeŸ���� ����� Ÿ�� �Ǵ� Ÿ�԰� �Ҳ� �̸��� �Է¹޾� entryPoint�� �����Ͽ� CreateNewNode()�� ȣ���ϰ�, ��ȯ���� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|
|�������� ��ȯ|Ÿ��:bool<br>true : �ڽĳ�� ������ �����߽��ϴ�.<br>false : �ڽĳ�� ������ ������ �߻��߽��ϴ�|

||GetChildNodeCount()|
|-|-|
|����|size_t GetChildNodeCount() const override;|
|����|entryPoint�� ������ GetChildNodeCount()�� ȣ���ϰ�, ��ȯ���� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|
|��ȯ|Ÿ��:size_t<br>�ڽĳ���� ����|

||Contains()|
|-|-|
|����|bool Contains(const std::string& key) const override;|
|����|const std::string&Ÿ���� Ű�� �Է¹޾� entryPoint�� ������ Contains()�� ȣ���ϰ�, ��ȯ���� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�� �Լ��� entryPoint�� ���� ��Ÿ�� ������ �߻��մϴ�.<br>ȣ�� ���� entryPoint�� Ȯ���� �ֽʽÿ�.|
|�Ű�����|const std::string&<br>�˻��� �̸�|
|��ȯ|Ÿ��:bool<br>true:�ִ�<br>false:����|

</details>
        

---

## Ŭ������ �뵵

RootNode�� �޸� ������ JSONTree������ �ϰ��� �������� �ʿ��ؼ� ����������ϴ�.

����� ���ø� ���ô�.

```
1. ���� JSONTreeBuilder���� ����� �������� �����Ҵ��ؼ�, �� �����͸� �Ѱ��־��ٰ� �����غ��ô�. 
    �׷���, ���� ���α׷��Ӱ� ���� �ڿ��� ������ �ؾ��ٸ� ��� �ɱ��?

2. ����, Ʈ�� a,b,c�� �ְ�, �ش� Ʈ������ ��Ʈ����� Ÿ���� �� �ٸ��ٸ� ��� �Ұǰ���?
```

RootNode�� ���� ��Ȳ���� ��ó�ϱ� ���� ����������ϴ�.

RootNode�� �ܺο��� �������� �����ϰų� �ִ� �Լ� ����, ���ο� ����� �������� �����Ҵ� �� �����ϴ� �Լ��� ��� �����ϰ�, RootNode��� ����� JSONTree�������� �������ν�
<br> ���� �� �������� ��ó�Ͽ����ϴ�.
    
����, ������ RootNode�� JSONTree�� �����ؼ� JSON�� ����ϱ⸸ �ϸ� �˴ϴ�.

RootNode�� JSONTree�� ��Ʈ����� �������̽� ���Ҹ��� �ϱ⿡, RootNode�� Ʈ���� �����Ѵٴ� �� JSONTree�� ��Ʈ��忡 �����Ѵٿ� �����ϴ�.

## Ŭ������ ���

�⺻������ ����ڴ� RootNode�� ���õ� ������ ���̺귯���� ���ֱ⿡,<br>����ڴ� JSONTree�� �����ϴ°� ����� RootNode�� ���� �����ؾ��ϴ� ���� ���� 2���� �����ϸ� ���� �����ϴ�.

����ڰ� RootNode�� ���� �����ؾ��ϴ� ��Ȳ�� ũ�� 2�����Դϴ�.

### 1. �ν��Ͻ�ȭ
���̺귯������ RootNode�� JSONTree�� �����ϱ� ���ؼ�, �⺻������ RootNode�� �ν��Ͻ��� �ʿ��մϴ�.

�̷� ����������, RootNode�� �ν��Ͻ��� �����ϰ�, JSONTreeBuilder�� �ν��Ͻ��� �ѱ�� �۾������� ����ڰ� �ؾ��մϴ�.

### 2. �޸� ����(RootNode�� �����Ҵ� ������츸)
���ÿ� �Ҵ��� ����, ������ �������� �ڵ����� �Ҹ��ڰ� ȣ�������, ���� �����Ҵ�� ���� �׷��� �ʽ��ϴ�.

���� RootNode ��ü�� �����Ҵ��ߴٸ�, �����Ҵ��� ���ҽ��� �����ϴ� �۾��� ����ڰ� �ؾ��մϴ�.

RootNode�� �����ϴ� �޸𸮴� JSONTree���Դϴ�.

�� ���̺귯���� �����⸦ ��� ���������� �ʽ��ϴ�.

### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "key": "value"
}
```


```cpp
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;

//RootNode�� ���ÿ����� ����
UglyJSONParser::RootNode root;

//������ ���� ������ RootNode�� Ÿ��
std::cout << static_cast<int>(root.GetNodeType()) << '\n';//��� Root(code : 6)

std::cout << parser.BuildJSONTreeFromFile(".\\testing\\json4.json", root) << '\n';//RootNode�� �ļ�(���ο��� JSONTreeBuilder�� �Է�)�� ������ �ѱ��.
//�׸��� ���ο����� root��忡 JSONTree�� ������ ������ �� ��带 �����Ҵ��ϴ� �Լ��� ȣ���Ѵ�.
//���: ����(true)

//������ ���� ������ RootNode�� Ÿ��
std::cout << static_cast<int>(root.GetNodeType()) << '\n';//��� Object(code : 1)

////////////
//RootNode�� ������ ����� �������̽� ������ �Ѵ�.
std::cout << "object key : " << root["key"].AsString() << '\n';//���:object key : value

root.DeleteChildNode("key");

std::cout << root.GetJsonTreeByString(); // ���:{}

///////////

//������ ��������, RootNode�� �Ҹ��ڰ� �ڵ����� ȣ��Ǿ�, �������� ������ JSONTree�� �����Ҵ��� �����ȴ�.
```

---

## <span style="color:red">����</span>

RootNode�� �������� �����ϴ� �Լ��� �����ϴ�.

����, Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

RootNode�� �⺻������ �������� nullptr�̱⿡, �ܵ����� ����ҽ� nullptr������ ��Ÿ�� ������ �߻��մϴ�.

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)