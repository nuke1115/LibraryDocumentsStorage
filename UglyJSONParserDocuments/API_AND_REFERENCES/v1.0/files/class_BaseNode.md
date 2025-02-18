# BaseNode (Base Class)  

### ���:
JSONTree�� ���Ǵ� Node���� ���̽� Ŭ����

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/NodeBase.hpp

### ����:
JSONTree�� ���Ǵ� ������ �⺻���� �Լ�,���������� �������̽��� �����մϴ�.

�� ��带 ��ӹ޴� ��� ���� Ŭ������ �ݵ�� BaseNode�� ��� ���� �����Լ��� �����ؾ��մϴ�.

���� Array�� Object���, �Ǵ� RootNode���� �ڽĳ����̳� ������ ��带 �����Ҷ� BaseNodeŸ���� ������ ���·� �����մϴ�.

�� ���� �ܵ����� �ν��Ͻ�ȭ �� �� ������(���� �����Լ��� ����), �ݵ�� �� ��带 ��ӹ޾� ������ ���� Ŭ������ ����Ű�� �����ͳ� ������ ���·� ���Ǿ�� �մϴ�.

�� Ŭ������ ��ӹ޾� ������ Ŭ����(��Ī ���)��� JSONTree�� �����մϴ�.

---

## �����

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

||BaseNode(string name, NodeType nodeType)|
|-|-|
|����|����� �̸��� Ÿ���� ���ڷ� �޾Ƽ�, ��忡 �����Ѵ�.|
|�Ű����� 1|Ÿ��:std::string<br>����� �̸�|
|�Ű����� 2|Ÿ��:UglyJSONParser::NodeType<br>����� Ÿ��|

||BaseNode(const BaseNode&)|
|-|-|
|Ư¡|������ �Լ�|

||BaseNode(BaseNode&&)|
|-|-|
|Ư¡|������ �Լ�|

||virtual ~BaseNode()|
|-|-|
|Ư¡|���� �Ҹ���|

</details>

---

### ����Լ�

<details>
<summary>��ġ��/����</summary>

||GetNodeType()|
|-|-|
|����|inline NodeType GetNodeType() const|
|����|����� Ÿ���� ��ȯ�Ѵ�.|
|��ȯ|Ÿ��:UglyJSONParser::NodeType<br>����� Ÿ��|

||GetName()|
|-|-|
|����|inline const string& GetName() const|
|����|����� �̸��� const ������ ��ȯ�Ѵ�.|
|��ȯ|Ÿ��:const std::string&<br>����� �̸�|

</details>

---

### ���� �����Լ�

�� �׸� ���ϴ� �Լ����� ���� �����Լ���, �� Ŭ������ ��ӹ޴� Ŭ�������� **����·ε�, ������ �����ؾ� �մϴ�.**

<details>
<summary>��ġ��/����</summary>

||virtual string GetJsonTreeByString() = 0|
|-|-|
|�⺻ �ǵ�|�� �Լ��� ȣ���� ��带 ��������, JSONTree�� �ϳ��� string���� ����ȭ�� ��ȯ�ϴ� �Լ��Դϴ�.|

||virtual const string& AsString() const = 0<br>virtual long long AsInt() const = 0<br>virtual bool AsBool() const = 0<br>virtual double AsDouble() const = 0|
|-|-|
|�⺻ �ǵ�|��忡�� �����͸� ���ö� ����ϴ� �Լ���|
|���ǻ���|Ÿ�Կ� ���� �ʴ� ��忡�� ȣ���Ұ��, ��Ÿ�� ������ �߻��Ѵ�.|
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||operator=()|  
|-|-|
|�����ε� 1|virtual void operator=(const string& strData) = 0|
|�����ε� 2|virtual void operator=(const char* strData) = 0|
|�����ε� 3|virtual void operator=(const long long intData) = 0|
|�����ε� 4|virtual void operator=(const bool boolData) = 0|
|�����ε� 5|virtual void operator=(const double doubleData) = 0|
|�⺻ �ǵ�|���� ��忡 �Ҵ��ϴ� �Լ���|  
|���ǻ���|Ÿ�Կ� ���� �ʴ� ���� �Ҵ��� ��� ��Ÿ�� ������ �߻��� �� ����.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||operator\[\]()|  
|-|-|
|�����ε� 1|virtual BaseNode& operator\[\](const string& strKey) = 0|
|�����ε� 2|virtual BaseNode& operator\[\](const size_t intKey) = 0|
|�⺻ �ǵ�|���� ���ڿ� Ű�� ���� Ű�� ����Ͽ� ��带 �����ϴ� �Լ���|  
|���ǻ���|�߸��� Ÿ���� Ű�� ����ϸ� ��Ÿ�� ������ �߻��� �� ����.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual void DeleteChildNode(const string& strKey) = 0<br>virtual void DeleteChildNode(size_t intKey) = 0|  
|-|-|  
|�⺻ �ǵ�|���� ���ڿ� Ű�� ���� Ű�� ����Ͽ� �ڽ� ��带 �����ϴ� �Լ���|  
|���ǻ���|�߸��� Ÿ���� Ű�� ����ϸ� ��Ÿ�� ������ �߻��� �� ����.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual bool CreateNewNode(NodeType type, string strKey) = 0<br>virtual bool CreateNewNode(NodeType type) = 0|  
|-|-|  
|�⺻ �ǵ�|�־��� Ÿ�԰� ���������� Ű�� ����Ͽ� ���ο� ��带 �����ϴ� �Լ���|  
|���ǻ���|object Ÿ���� ��� Ű�� ��ġ�� ��Ÿ�� ������ �߻��Ѵ�.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual size_t GetChildNodeCount() const = 0
|-|-|
|�⺻ �ǵ�|�� �Լ��� ȣ���� ����� �ڽĳ���� ������ ���´�|
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual void Clear() = 0|
|-|-|
|�⺻ �ǵ�|�� �Լ��� ȣ���� ����� ��� �ڽĳ�带 �����Ѵ�|
|���ǻ���|array �Ǵ� object��尡 �ƴҽ� ��Ÿ�� ������ �߻��Ѵ�.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual std::vector<BaseNode*>& GetChildNodeVector() = 0|
|-|-|
|�⺻ �ǵ�|�� �Լ��� ȣ���� ����� �ڽĳ�� �����͸� �����ϴ� ���͸� ��ȯ�Ѵ�|
|���ǻ���|array �Ǵ� object��尡 �ƴҽ� ��Ÿ�� ������ �߻��Ѵ�.|  
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

||virtual bool Contains(const string& key) const = 0|
|-|-|
|�⺻ �ǵ�|�ӷ����� ���� ���ڿ��� ��ġ�ϴ� �̸��� ������ ��尡 childNodeVector�� �ִ��� �˻��Ѵ�|
||�ڼ��� ������ �� ���� Ŭ������ �����Ǿ��ִ�.|

</details>

---

### protected ������� �� using����

<details>
<summary>��ġ��/����</summary>

||using string = std::string|
|-|-|
|����|stringŸ�� ������ std���� ���ϰ� �����Ϸ��� �����ߴ�|

||string _nodeName|
|-|-|
|����|����� �̸��� �����Ѵ�|

||NodeType _nodeType|
|-|-|
|����|����� Ÿ���� �����Ѵ�|

</details>

-----

### �� Ŭ������ ��ӹ޴� Ŭ������

<details>
<summary>��ġ��/����</summary>

[ArrayNode (Class, Derived from BaseNode)](class_ArrayNode.md)

[BoolNode (Class, Derived from BaseNode)](class_BoolNode.md)

[NullNode (Class, Derived from BaseNode)](class_NullNode.md)

[NumberNode (Class, Derived from BaseNode)](class_NumberNode.md)

[ObjectNode (Class, Derived from BaseNode)](class_ObjectNode.md)

[RootNode (Class, Derived from BaseNode)](class_RootNode.md)

[StringNode (Class, Derived from BaseNode)](class_StringNode.md)

</details>

---

## Ŭ������ �뵵

�� Ŭ������ �⺻������ �������� ���� �������̽� �������� �ۼ��Ǿ����ϴ�.

�׷��⿡, �� Ŭ������ �ܵ����� �ν��Ͻ�ȭ �� �� ����,
�� Ŭ������ ��ӹ޾Ƽ� �����ϰų� ,�� Ŭ������ ��ӹ޴� Ŭ������ ����Ű�� ������ �����ͷνḸ ���˴ϴ�.

## Ŭ������ ���

```cpp

//���õ�

BaseNode* CreateNode(NodeType type, std::string name); //��带 �����ϰ�, ��ĳ�����ؼ� ��ȯ�ϴ� �뵵�� ���

class ObjectNode : public BaseNode //�������� �ϴ� �뵵�� ���
{
private:
    std::vector<BaseNode*> _childNodeVector; //������ ��ĳ�����Ͽ� �Ѱ��� �����ϴ� �뵵�� �����ͷ� ���
    NodeFactory _factory;
public:
    //�޼����
};

BaseNode node; // �߸��� ���

BaseNode node2 = new ObjectNode("�̸�",NodeType::Object); // �ùٸ� ���

```

---

## <span style="color:red">����</span>

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)