# JSONTreeBuilder (class)

### ���:

JSONTree�� �������ִ� ����� ���ִ� Ŭ����

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/JSONTree/JSONTreeBuilder.hpp

### ����:

JSONTree�� �����ϱ� ���� ������� Ŭ����.

JSONTree�� �����ϱ� ���� ���ο� ���� �Լ����� ����Ǿ��ֽ��ϴ�.

�׸��� �� �Լ����� BuildJSONTree()���� ȣ���ϸ� JSONTree�� �����մϴ�.

## �����:

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

||JSONTreeBuilder()|
|-|-|
|Ư¡|�⺻ ������|

||JSONTreeBuilder(const JSONTreeBuilder&)|
|-|-|
|Ư¡|�⺻ ���������|

||JSONTreeBuilder(JSONTreeBuilder&&)|
|-|-|
|Ư¡|�⺻ �̵�������|

||~JSONTreeBuilder()|
|-|-|
|Ư¡|�⺻ �Ҹ���|

</details>

### ����Լ�

<details>
<summary>��ġ��/����</summary>

||BuildJSONTree()|
|-|-|
|����|bool BuildJSONTree(RootNode& rootNode, const std::list<std::string>& tokens);|
|����|�Ű������� ���� ��Ʈ��忡, �Ű������� ���� ��ū��� JSONTree�� �����մϴ�. �׸��� ��� ��ȯ|
|�Ű����� 1|Ÿ��:UglyJSONparser::RootNode&<br>JSONTree�� ����� ������|
|�Ű����� 2|const std::list<std::string>&<br>��ū��|
|��ȯ|bool<br>true:JSONTree���忡 �����߽��ϴ�.<br>false:JSONTree���� ������ ������ ������ϴ�.|
|false�� �ߴ� ���|1.RootNode�� ������� �ʴ�.|
||2.��ū�� ������ �ִ�.(ex.��ȣ ¦�� ����,�� ���� ����)|
||3.��� ������ �����ߴ�.|

</details>

## �뵵 �� ���

��ūȭ�� ���ڵ��� �޾� RootNode�� JSONTree�� �������ִ� ������ �մϴ�.

�� Ŭ������ UglyJSONParser���ο��� ���˴ϴ�.

����, �� Ŭ������ Tokenizer���� ������ ��ū�� ����Ѵٴ� ���� �Ͽ� �ۼ��Ǿ���,<br>�� Ŭ������ ���� ����� ���� ������ JSONParser Ŭ������ �����ξ����ϴ�.

����, ����ڰ� �� Ŭ������ ���� ����� ��Ȳ�� ���� �����ϴ�.

### ����

```json
{
    "asdf": "value"
}
```

```cpp
//�ʿ��� ������ ����
FileIOManager mgr;
JSONTreeBuilder builder;
Tokenizer tokenizer;
RootNode root;
std::string str;
std::list<std::string> tokens;

mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json");//json������ �ε��Ѵ�.

tokenizer.Tokenize(str, tokens);//���ڿ��� ��ūȭ�Ѵ�.
    
std::cout << builder.BuildJSONTree(root, tokens) << '\n';//��ū���� �̿��� root�� JSONTree ����
//��� : 1

std::cout << root.GetJsonTreeByString() << '\n';// ��� : {"asdf":"value"}
std::cout << root["asdf"].AsString() << '\n';//��� : value
```

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)