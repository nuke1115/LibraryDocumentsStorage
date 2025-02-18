# ArrayNode (class, Derived from BaseNode)

### ���:
JSON�� Value�� Array������ Value�� ǥ���ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/Node.hpp �� 190��° ��

### ����:
JSON�� Value�� Array������ Value�� ǥ���ϱ� ����, BaseNodeŬ������ ��ӹ޾� ������ ����Դϴ�.

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::Array�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

ObjectNode�� ����������, �ش� ��忡�� ���� �����ϴ� �����ڸ� ����� �� ��Ÿ�� ������ �߻��մϴ�.

�׷���, �ڽĳ�忡 �����ϰ� �����ϴ� �Լ��� ��� �����մϴ�.

���� std::vector�� BaseNode�� ������ ���·� �ڽ� ������ ���� �����ϸ�, �̷��� �ڽ� ���鿡�� size_t Ÿ���� ������ Ű������ �̿��� []�� ���� �����մϴ�.

���� ���ڿ��� Ű������ ����Ϸ��� �õ��ϰų�, �־��� Ű���� �ε����� ������ �Ѿ�� ��Ÿ�� ������ �߻��մϴ�.

ObjectNode�� �ٸ���, ���ο� �ڽĳ�带 �����Ҷ� ����� �̸��� �ο������� �ʾƵ� ����� �����ϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||ArrayNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Array��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||ArrayNode(const ArrayNode&)|
|-|-|
|����|������ �Լ�|

||ArrayNode(ArrayNode&&)|
|-|-|
|����|������ �Լ�|

||~ArrayNode()|
|-|-|
|����|�Ҹ��ڰ� ȣ��Ǹ�, Clear() �Լ��� ȣ���ϰ�,<br>�ڽĳ�尡 Object�� ArrayŸ���̸� Clear()�Լ��� ��������� ȣ���Ͽ�<br>��� �ڽĳ����� �����մϴ�.|

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
|����|�Լ��� ȣ������� ostringstream (���� buffer��� �Ѵ�)�� ([)�� �Է��ϰ�, ��ȯ ������ (])�� �Է��մϴ�.|
||�׸��� BaseNode�� ��ĳ���õ� �ڽĳ���� �����͸� �����ϴ� ����(���� childNodeVector�� Ī��)�� ��ȸ�ϸ�,<br>�ڽĳ����� ������� GetJsonTreeByString() �Լ��� ����ȣ���Ͽ�<br>�� ��ȯ���� buffer�� �Է��Ѵ�.|
||���� ���� �ڽĳ�尡 childNodeVector�� ������ ���Ұ� �ƴ϶��, buffer�� (,)�� �Է��Ѵ�|
||childNodeVector��ȸ�� �����ٸ� ���������� buffer�� (])�� �Է��ϰ�, buffer�� .str()�Լ��� ȣ���Ͽ� ���ڿ��� ��ȯ�޾� ���ڿ��� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:std::string<br>�� ��带 �������� �� ��� ���� ���� ������ ����ȭ�� ���ڿ�|

||operator\[\]()|
|-|-|
|�����ε� 2|BaseNode& operator\[\](const size_t intKey) override;|
|����|�� �����ε�� size_t Ÿ���� ���� �ε����� �Է¹޾�, ������ childNodeVector���� �ش� �ε����� �ڽĳ�� �����͸� �����մϴ�.|
|<span style="color:red">����</span>|���� �Է� �ε����� childNodeVector�� ũ�⺸�� ���ų� ũ�ٸ� ��Ÿ�� ������ �߻��մϴ�.<br>�ݵ�� �ε����� Ȯ���Ͽ� �ֽʽÿ�.|
|�Ű�����|Ÿ��:size_t<br>������ ������ ����� �ε���|
|��ȯ|Ÿ��:UglyJSONParser::BaseNode&<br>�ڽĳ���� ����|
  
||GetChildNodeVector()|
|-|-|
|����|std::vector<BaseNode*>& GetChildNodeVector() override;|
|����|childNodeVector�� ������ ��ȯ�մϴ�.|
|��ȯ|Ÿ��:std::vector\<UglyJSONParser::BaseNode*\>&<br>childNodeVector�� ����|

||Clear()|
|-|-|
|����|void Clear() override;|
|����|�� �Լ��� ��������� ȣ���ϸ�, �ڽ��� �������� ��� �ڽĳ�带 �����մϴ�.|
|�۵�|�� �Լ��� ȣ��Ǹ�, childNodeVector�� ��ȸ�ϸ�, ���� object �Ǵ� arrayNode���, Clear()�Լ��� ���ȣ���ϰ�, �ƴ϶�� �����մϴ�. |
||�׸��� ������ ������ childNodeVector.clear()�� ȣ���Ͽ� ���͸� ���� �Լ��� �����մϴ�.|
|Ư¡|�Ҹ�ÿ� �ڵ����� ȣ���|

||DeleteChildNode()|
|-|-|
|�����ε� 2|void DeleteChildNode(size_t intKey) override;|
|����|�� �����ε�� size_t Ÿ���� ���� �ε����� �Է¹޾�, ������ childNodeVector���� �ش� �ε����� �ڽĳ�带 �����մϴ�.|
|<span style="color:red">����</span>|���� �Է� �ε����� childNodeVector�� �ִ� �ε������� ���ų� ũ�ٸ� ��Ÿ�� ������ �߻��մϴ�.<br>�ݵ�� �ε����� Ȯ���Ͽ� �ֽʽÿ�.|
|�Ű�����|Ÿ��:size_t<br>������ ����� �ε���|

||CreateNewNode()|
|-|-|
|�����ε� 1|bool CreateNewNode(NodeType type, string strKey) override;|
|����|�� �����ε�� ����� Ÿ�԰� ���ڿ��� �� ����� �̸��� �Է¹޾�, ����� Ÿ�Ը� �޴� �����ε带 ȣ���մϴ�.|
||ArrayNode�� �ڽĳ�带 ���ڿ��� �� �̸��� �ƴ�, �ε����� �����ϱ⿡ �����Ѱ̴ϴ�.|
|�Ű�����|Ÿ��:UglyJSONParser::NodeType, std::string<br>������ ����� Ÿ�԰� �̸�|
|��ȯ|Ÿ��:bool<br>true : �ڽĳ�� ������ �����߽��ϴ�.<br>false : �ڽĳ�� ������ ������ �߻��߽��ϴ�|
|false�� ��ȯ�Ǵ� ����|1. ����� �����Ҵ翡 ����|

||CreateNewNode()|
|-|-|
|�����ε� 2|bool CreateNewNode(NodeType type) override;|
|����|�� �����ε�� ����� Ÿ���� �Է¹޾�, NodeFactory�� ���� Ÿ�԰� nullName�̶�� ���ڿ� �̸��� �־ �ڽĳ�� ������ �õ��մϴ�.<br>�����ϸ� childeNodeVector�� push�մϴ�.|
|�Ű�����|Ÿ��:UglyJSONParser::NodeType<br>������ ����� Ÿ��|
|��ȯ|Ÿ��:bool<br>true : �ڽĳ�� ������ �����߽��ϴ�.<br>false : �ڽĳ�� ������ ������ �߻��߽��ϴ�|
|false�� ��ȯ�Ǵ� ����|1. ����� �����Ҵ翡 ����|

||GetChildNodeCount()|
|-|-|
|����|size_t GetChildNodeCount() const override;|
|����|childNodeVector.size() �� ����� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:size_t<br>�ڽĳ���� ����|

||Contains()|
|-|-|
|����|bool Contains(const std::string& key) const override;|
|Ư¡|�׻� false�� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:bool<br>true:�ִ�<br>false:����|
|�Ű�����|const std::string&<br>�˻��� �̸�|

</details>
        
���⿡ ���� �Լ��� ��������� �̿ܿ��� ȣ��� ��Ÿ�� ������ �߻��մϴ�.

---

## Ŭ������ �뵵

ArrayNode�� �⺻�����δ� ObjectNode�� ���� **�Ѱ��� ��忡 ���� ��带 �����ϰ� ������ ��** ����մϴ�.

ArrayNode�� �Ϲ����� array�ڷᱸ���� ����ϰ�, �ַ� **���� ������ �ڷᰡ �������� ������** ����մϴ�.

����, ���� �ٸ� ������ �ڷᵵ ���� ����������, ���� ��õ������ �ʴ� ����Դϴ�.

## Ŭ������ ���

�⺻������ RootNode�� ������ ��� ������ ����ڰ� ���� �ν��Ͻ�ȭ �� �ʿ䰡 ������ ���̺귯���� ����Ǿ��ֽ��ϴ�.

ArrayNode�� ObjectNode������ ��� ������ ������ ũ�� 3������ �ֽ��ϴ�.

### 1. �ڽĳ�� ����(����/����)
�� ������ ���ϴ� �Լ����� CreateNewNode()�� DeleteChildNode(), Clear() �� �ֽ��ϴ�.

�� �Լ����� �ڽĳ�带 �����ϰų� �����Ҷ� ����ϴ� �Լ����,<br>CreateNewNode()�� DeleteChildNode()�� JSON�����͸� �б⸸ �ϴ°��� �ƴ�, ���� �����ؾߵǴ� ���α׷��� ���鶧 ���� ����Ұ��Դϴ�.

Clear()�Լ��� ���� �ش� ��尡 �Ҹ��Ҷ� �ڵ����� ȣ��Ǳ⿡, �Ϲ����� ��Ȳ������ ����� ���� �״��� ������ �����̴ϴ�.

### 2. �ڽĳ�� ����

�� ������ ���ϴ� �Լ��� operator\[\](size_t) �Լ��� �ֽ��ϴ�.

### 3. �ڽĳ�� ����� ����

�� ������ ���ϴ� �Լ��δ� GetChildNodeVector()�� GetChildNodeCount() �� �ֽ��ϴ�.

�� GetChildNodeVector()�Լ��� Iterator�� ���������� ����ϱ� ���� ������� �Լ��Դϴ�.

ArrayNode�� ���� GetChildNodeCount() �Լ��� for ������ ����ϱ⿡, ���� ����� �ʿ�� �����ϴ�.


### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "arr": [
        1,
        2,
        3
    ],
    "str_arr": [
        "asdf",
        "asdf2",
        "asdf3"
    ],
    "obj_arr": [
        { "key": 1 },
        { "key": 2 },
        {"key": 3}
    ]
}
```


```cpp

//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;

//json���Ͽ��� ������ �о�� root��忡 JSONTree ����
parser.BuildJSONTreeFromFile(".\\testing\\json2.json", root);

/////////////////
//�ڽĳ�� ����
std::cout << "arr 0 : " << root["arr"][0].AsInt() << '\n';//��� : arr 0 : 1
std::cout << "str_arr 0 : " << root["str_arr"][0].AsString() << '\n';//��� : str_arr 0 : asdf
std::cout << "obj_arr 0 key : " << root["obj_arr"][0]["key"].AsInt() << '\n';//��� : obj_arr 0 key : 1

std::cout << "arr operator[]() return type : " << typeid(root["arr"][0]).name() << '\n';//��� : arr operator[]() return type : class UglyJSONParser::NumberNode
/*
operator[](size_t) �����ε��, �ε����� ���� ��ġ�� �ڽĳ���� ������ ��ȯ�մϴ�. 
*/
//////////////////

/////////////////
//�ڽĳ�� ����
//1. �ڽĳ�� ����
std::cout << root["arr"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ArrayNode ���� //��� : [1,2,3]

std::cout << root["arr"].CreateNewNode(UglyJSONParser::NodeType::Number) << '\n';//true : ����, false : ���� //��� : 1

std::cout << root["arr"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ArrayNode ���� //��� : [1,2,3,0]

//2. �ڽĳ�� ����

std::cout << root["str_arr"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ArrayNode ���� //��� : ["asdf","asdf2","asdf3"]

root["str_arr"].DeleteChildNode(2);//2�� �ε���(3��°)�� �ڽĳ�� ����

std::cout << root["str_arr"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ArrayNode ���� //��� : ["asdf","asdf2"]

////////////////////
    
////////////////////
//�ڽĳ�� ����� ����

std::cout << root["obj_arr"].GetJsonTreeByString() << '\n';//��� : [{"key":1},{"key":2},{"key":3}]
std::cout << typeid(root["obj_arr"].GetChildNodeVector()).name() << '\n';// childNodeVector //��� : class std::vector<class UglyJSONParser::BaseNode * __ptr64,class std::allocator<class UglyJSONParser::BaseNode * __ptr64> >
std::cout << root["obj_arr"].GetChildNodeCount();// �ڽĳ���� ���� //��� : 3

```

---

## <span style="color:red">����</span>

string Ű�� �����ϴ°��� ������ �ʽ��ϴ�. �õ��ϸ� ��Ÿ�� ������ �߻��մϴ�.

����, ����ϴ� ���� �ε����� 0���� �۰ų�, childNodeVector�� ũ��� ���ų� ũ�� ��Ÿ�� ������ �߻��մϴ�.

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ����� ArrayNode���� ȣ��� ��Ÿ�� ������ �߻��ϴ� �Լ��� �Դϴ�.

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

||DeleteChildNode()|
|-|-|
|�����ε� 1|void DeleteChildNode(const string& strKey) override;|

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)