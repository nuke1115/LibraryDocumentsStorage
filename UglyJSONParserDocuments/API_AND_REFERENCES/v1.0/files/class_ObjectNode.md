# ObjectNode (class, Derived from BaseNode)

### ���:
JSON�� Value�� Object������ Value�� ǥ���ϱ� ���� ������� ���

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/JSONTree/Node.hpp �� 147��° ��

### ����:
JSON�� Value�� Object������ Value�� ǥ���ϱ� ����, BaseNodeŬ������ ��ӹ޾� ������ ����Դϴ�.

BaseNode�� ��ӹ޾ұ⿡, BaseNodeŸ���� �����ͳ� ������ ����ų �� �ֽ��ϴ�.

NodeTypes�� Nodetype::Object�� ����� enum �ڵ尡 ���ǵǾ��ֽ��ϴ�.

ArrayNode�� ����������, �ش� ��忡�� ���� �����ϴ� �����ڸ� ����� �� ��Ÿ�� ������ �߻��մϴ�.

�׷���, �ڽĳ�忡 �����ϰ� �����ϴ� �Լ��� ��� �����մϴ�.

���� std::vector�� BaseNode�� ������ ���·� �ڽ� ������ ���� �����ϸ�, �̷��� �ڽ� ���鿡�� std::stringŸ���� ���ڿ��� Ű������ �̿��� []�� ���� �����մϴ�.

���� size_tŸ���� ������ Ű������ ����Ϸ��� �õ��ϰų�, �־��� Ű���� �̸����� ������ ��尡 BaseNode�� ��ĳ���õ� �ڽĳ���� �����͸� �����ϴ� ����(���� childNodeVector�� Ī��)�� ���ٸ� ��Ÿ�� ������ �߻��մϴ�.

ArrayNode�� �ٸ���, ���ο� �ڽĳ�带 �����Ҷ� ����� �̸��� �ο������� ������, ��Ÿ�� ������ �߻��մϴ�.

---

## �����

### ������ �� �Ҹ���
<details>
<summary>��ġ��/����</summary>

||ObjectNode(string name)|
|-|-|
|����|����� �̸��� �ް�, �װͰ� Nodetype::Object��� enum������� BaseNode �����ڿ� ������, ����� �̸��� Ÿ���� �����մϴ�.|
|�Ű�����|Ÿ��:std::string<br>����� �̸�|

||ObjectNode(const ObjectNode&)|
|-|-|
|����|������ �Լ�|

||ObjectNode(ObjectNode&&)|
|-|-|
|����|������ �Լ�|

||~ObjectNode()|
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
|����|�Լ��� ȣ������� ostringstream (���� buffer��� �Ѵ�)�� ({)�� �Է��ϰ�, ��ȯ ������ (})�� �Է��մϴ�.|
||childNodeVector�� ��ȸ�ϸ�, �ڽĳ���� �̸�, (:), �ڽĳ���� ������ ������ buffer�� �Է��Ѵ�.|
||���� ���� �ڽĳ�尡 ������ ��尡 �ƴ϶��, (,)�� buffer�� �Է��Ѵ�.|
||childNodeVector��ȸ�� �����ٸ� ���������� buffer�� (})�� �Է��ϰ�, buffer�� .str()�Լ��� ȣ���Ͽ� ���ڿ��� ��ȯ�޾� ���ڿ��� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:std::string<br>�� ��带 �������� �� ��� ���� ���� ������ ����ȭ�� ���ڿ�|


||operator\[\]()|
|-|-|
|�����ε� 1|BaseNode& operator\[\](const string& strKey) override;|
|����|�� �����ε�� const std::string& Ÿ���� ���ڿ��� �Է¹޾�, ��ġ�ϴ� �̸��� ���� ��带 childNodeVector���� ã�� ������ ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�Է��� ���ڿ��� �̸����� ������ ��尡 childNodeVector�� ���ٸ� ��Ÿ�� ������ �߻��մϴ�.<br>�Է��� ���ڿ��� �ִ°� �´��� Ȯ���Ͻñ� �ٶ��ϴ�.|
|�Ű�����|Ÿ��:const std::string&<br>ã�� ����� �̸�|
  
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
|�����ε� 1|void DeleteChildNode(const string& strKey) override;|
|����|�� �����ε�� const string& strKey Ÿ���� ���ڿ� Ű�� �Է¹޾�, ������ childNodeVector���� �ش� Ű�� ���� �̸��� ������ �ڽĳ�带 �����մϴ�.|
|<span style="color:red">����</span>|���� �Է� Ű�� �̸����� ������ ��尡 childNodeVector�� ���ٸ� ��Ÿ�� ������ �߻��մϴ�.<br>�ݵ�� Ű�� Ȯ���Ͽ� �ֽʽÿ�.|
|�Ű�����|Ÿ��:const std::string<br>������ ����� �̸�|


||CreateNewNode()|
|-|-|
|�����ε� 1|bool CreateNewNode(NodeType type, string strKey) override;|
|����|�� �����ε�� ����� Ÿ�԰� ���ڿ��� �� ����� �̸��� �Է¹޾�,���� childNodeVector�� ��ġ�� �̸��� �ִ��� �˻��մϴ�.|
||���ٸ�, NodeFactory�� Ÿ�԰� �̸��� �־ ��� ������ �õ��ϰ�, �����Ѵٸ� childNodeVector�� push�մϴ�|
|�Ű�����|Ÿ��:UglyJSONParser::NodeType, std::string<br>������ ����� Ÿ�԰� �̸�|
|��ȯ|Ÿ��:bool<br>true : �ڽĳ�� ������ �����߽��ϴ�.<br>false : �ڽĳ�� ������ ������ �߻��߽��ϴ�|


||GetChildNodeCount()|
|-|-|
|����|size_t GetChildNodeCount() const override;|
|����|childNodeVector.size() �� ����� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:size_t<br>�ڽĳ���� ����|

||Contains()|
|-|-|
|����|bool Contains(const std::string& key) const override;|
|����|�Է����� ���� Ű�� ��ġ�ϴ� �̸��� ������ ��尡 childNodeVector�� �ִ��� �˻��ϰ� ����� ��ȯ�Ѵ�.|
|��ȯ|Ÿ��:bool<br>true:�ִ�<br>false:����|
|�Ű�����|const std::string&<br>�˻��� �̸�|

</details>

���� ���� �Լ� �̿��� �Լ��� �� ��忡�� ȣ��� ��Ÿ�� ������ �߻��մϴ�.

---

## Ŭ������ �뵵

ObjectNode�� �⺻�����δ� ArrayNode�� ���� **�Ѱ��� ��忡 ���� ��带 �����ϰ� ������ ��** ����մϴ�.

ObjectNode�� �Ϲ����� dictionary�� ����ϰ�, key-value������ ���� ����������, **�ַ� ���� �ٸ� ���� �����ҋ� ����մϴ�.**

## Ŭ������ ���

�⺻������ RootNode�� ������ ��� ������ ����ڰ� ���� �ν��Ͻ�ȭ �� �ʿ䰡 ������ ���̺귯���� ����Ǿ��ֽ��ϴ�.

ArrayNode�� ObjectNode������ ��� ������ ������ ũ�� 3������ �ֽ��ϴ�.

### 1. �ڽĳ�� ����(����/����)
�� ������ ���ϴ� �Լ����� CreateNewNode()�� DeleteChildNode(), Clear() �� �ֽ��ϴ�.

�� �Լ����� �ڽĳ�带 �����ϰų� �����Ҷ� ����ϴ� �Լ����,<br>CreateNewNode()�� DeleteChildNode()�� JSON�����͸� �б⸸ �ϴ°��� �ƴ�, ���� �����ؾߵǴ� ���α׷��� ���鶧 ���� ����Ұ��Դϴ�.

Clear()�Լ��� ���� �ش� ��尡 �Ҹ��Ҷ� �ڵ����� ȣ��Ǳ⿡, �Ϲ����� ��Ȳ������ ����� ���� �״��� ������ �����̴ϴ�.

### 2. �ڽĳ�� ����

�� ������ ���ϴ� �Լ��� operator\[\](const std::string&) �Լ��� �ֽ��ϴ�.

### 3. �ڽĳ�� ����� ����

�� ������ ���ϴ� �Լ��δ� GetChildNodeVector()�� GetChildNodeCount() �� �ֽ��ϴ�.

�� GetChildNodeVector()�Լ��� Iterator�� ���������� ����ϱ� ���� ������� �Լ��Դϴ�.

ObjectNode�� ���� v1.0���� Iterator�� �������� �ʱ⿡, �� �Լ��� Iterator�� ���������� ����մϴ�.


### ����

������ ���õ��Դϴ�.

���� json ����:
```json
{
    "obj1": {
        "key": 1,
        "key2": "value",
        "key3": true,
        "key4": null
    },
    "obj2": {
        "key": [
            1,2,3
        ],
        "object": {
            "key" : "value" 
        }
    },
    "obj3": {
    }
}
```


```cpp
//�ʿ��� ������ ����
UglyJSONParser::JSONParser parser;
UglyJSONParser::RootNode root;

//json���Ͽ��� ������ �о�� root��忡 JSONTree ����
parser.BuildJSONTreeFromFile(".\\testing\\json3.json", root);

/////////////////
//�ڽĳ�� ����

std::cout << "obj1 key : " << root["obj1"]["key"].AsInt() << '\n';//��� : obj1 key : 1
std::cout << "obj1 key2 : " << root["obj1"]["key2"].AsString() << '\n';//��� : obj1 key2 : value
std::cout << "obj1 key3 : " << root["obj1"]["key3"].AsBool() << '\n';//��� : obj1 key3 : 1

std::cout << "obj operator[]() return type : " << typeid(root["obj1"]).name() << '\n';//��� : obj operator[]() return type : class UglyJSONParser::ObjectNode
/*
operator[](const std::string&) �����ε��, �Է����� ���� �̸��� ���� �̸��� �ڽĳ���� ������ ��ȯ�մϴ�.
*/
//////////////////

/////////////////
//�ڽĳ�� ����
//1. �ڽĳ�� ����
std::cout << root["obj3"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ObjectNode ���� //��� : {}

std::cout << root["obj3"].CreateNewNode(UglyJSONParser::NodeType::Number, "new number node") << '\n';//true : ����, false : ���� //��� : true

std::cout << root["obj3"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ObjectNode ���� //��� : {"new number node":0}


//2. �ڽĳ�� ����
std::cout << root["obj2"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ObjectNode ���� //��� : {"key":[1,2,3],"object":{"key":"value"}}

root["obj2"].DeleteChildNode("object");//2�� �ε���(3��°)�� �ڽĳ�� ����

std::cout << root["obj2"].GetJsonTreeByString() << '\n';// �ڽĳ�� ���� ������ ObjectNode ���� //��� : {"key":[1,2,3]}

////////////////////

////////////////////
//�ڽĳ�� ����� ����
std::cout << root["obj3"].GetJsonTreeByString() << '\n';//��� : {"new number node":0}
std::cout << typeid(root["obj3"].GetChildNodeVector()).name() << '\n';// childNodeVector //��� : class std::vector<class UglyJSONParser::BaseNode * __ptr64,class std::allocator<class UglyJSONParser::BaseNode * __ptr64> >
std::cout << root["obj3"].GetChildNodeCount();// �ڽĳ���� ���� //��� : 1
```

---

## <span style="color:red">����</span>

���� �ε����� ����ϴ°��� ������ ������, �õ��ϸ� ��Ÿ�� ������ �߻��մϴ�.

���� �Է��� ���ڿ��� �̸����� ������ ��尡 �������� ������ ��Ÿ�� ������ �߻��մϴ�.

��� ���� Contains() �Լ��� Ȯ���Ͻʽÿ�.

Ʈ�� ����� �ν��Ͻ��� �ٸ� ������ �����ϴ°��� ����������, �����ͷ� ���ټ����� �����ϴ°��� ������� �ʽ��ϴ�.

���� �Լ� �� �����ε���� ObjectNode���� ȣ��� ��Ÿ�� ������ �߻��մϴ�.

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
|�����ε� 2|BaseNode& operator\[\](const size_t intKey) override;|

||DeleteChildNode()|
|-|-|
|�����ε� 2|void DeleteChildNode(size_t intKey) override;|

||CreateNewNode()|
|-|-|
|�����ε� 2|bool CreateNewNode(NodeType type) override;|
|<span style="color:red">����</span>|�� object�� std::stringŸ���� �̸����� ������ �ʿ��ϱ⿡, �� �����ε�� �׻� false�� ��ȯ�մϴ�.|
|��ȯ|Ÿ��:bool<br>false : �ڽĳ�� ������ ������ �߻��߽��ϴ�|
|�Ű�����|Ÿ��:UglyJSONParser::NodeType<br>������ ����� Ÿ��|

# ���ư���

[BaseNode (Base Class)](class_BaseNode.md)