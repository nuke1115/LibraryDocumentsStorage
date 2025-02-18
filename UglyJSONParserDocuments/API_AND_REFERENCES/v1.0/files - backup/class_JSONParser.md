# JSONParser(class)

### ���:

JSON������ �аų� ����, JSONTree�� �����ϴ� �Ϸ��� ������ ���ϰ� ����ϴ°��� �����ִ� Ŭ����

### ���ǵ� ���� �� ��ġ :

Include/UglyJSONParser/JSONParser/JSONParser.hpp

### ���� :

JSONParser�� UglyJSONParser�� JSON�� �а�,����,JSONTree�� �����ϴ� �Ϸ��� ����� ���ϰ� ��� �����ϰ� ���ݴϴ�.

�̸� ���� �� ����� ����ϴ� Ŭ�������� ����� ������, �̵��� �� ������ �°� ȣ���ϴ� �Լ����� ������ �ֽ��ϴ�.

�� Ŭ������ ����, ����ڴ� � �Լ��� � Ÿ�ֿ̹� ȣ���ϰ�, � �ӽú����� �ʿ����� �Ű澲�� �ʾƵ� �˴ϴ�.

## �����:

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

|| JSONParser()|
|-| -|
|Ư¡ | �⺻ ������|

||JSONParser(const JSONParser&)|
|-| -|
|Ư¡ | �⺻ ���������|

||JSONParser(JSONParser&&)|
|-| -|
|Ư¡ | �⺻ �̵�������|

||~JSONParser()|
|-| -|
|Ư¡ | �⺻ �Ҹ��� |

</details>

### ����Լ�

<details>
<summary>��ġ��/��</summary>

||BuildJSONTreeFromFile()|
|-|-|
|����|bool BuildJSONTreeFromFile(const string& FilePath, RootNode& rootNode);|
|����|�Ű������� ���� ���� ��ġ���� ������ �о��, �Ű������� ���� RootNode�� JSONTree�� �����Ѵ�. �׸��� ��� ��ȯ|
|�Ű����� 1|Ÿ��:const std::string&<br>�о�� json�� ���|
|�Ű����� 2|Ÿ��:RootNode&<br>JSONTree�� ����� ������|
|��ȯ|Ÿ��:bool<br>true:���� ����<br>false:���� �������� ���� �߻�|
|false�� ������ ����|1. ���� ��ο� ������ ����.|
||2. FileIOManager�� ���� �о���� ����|
||2-1. ifstream�� ������ �ʾҴ�.|
||2-2. ������ ����.|
||3. BuildJSONTreeFromString()�Լ��� ����.<br>�� ������ �ٷ� �ؿ� false�� ������ ������ �ִ�.|

||BuildJSONTreeFromString()|
|-|-|
|����|bool BuildJSONTreeFromString(const string& sourceString, RootNode& rootNode);|
|����|�Ű������� ���� ���ڿ����� JSONTree�� �Ű������� ���� RootNode�� �����Ѵ�. �׸��� ��� ��ȯ|
|�Ű����� 1|Ÿ��:const std::string&<br>JSONTree�� ������ ���ڿ�|
|�Ű����� 2|Ÿ��:RootNode&<br>JSONTree�� ����� ������|
|��ȯ|Ÿ��:bool<br>true:���� ����<br>false:���� �������� ���� �߻�|
|false�� ������ ����|1. ���ڿ��� ����ִ�.|
||2. Tokenizer�� ��ūȭ ����|
||2-1. �Էµ� ���ڿ��� ��ūȭ �ϴ� ��������, �ùٸ��� ���� ������ �ִٴ°� ����|
||3. JSONTreeBuilder�� JSONTree ���� ����|
||3-1. RootNode�� ������� �ʴ�.|
||3-2. ��ū�� ������ �ִ�.(ex.��ȣ ¦�� ����,�� ���� ����)|
||3-3. ��� ������ �����ߴ�.|

||SaveJSONTreeToFile()|
|-|-|
|����|bool SaveJSONTreeToFile(const string& FilePath, RootNode& rootNode);|
|����|�Ű������� ���� ���Ͽ�, �Ű������� ���� RootNode���� JSONTree�� ����ȭ�� ����. �׸��� ��� ��ȯ|
|�Ű����� 1|Ÿ��:const std::string&<br>�����͸� ������ json�� ���|
|�Ű����� 2|Ÿ��:RootNode&<br>JSONTree���� ������|
|��ȯ|Ÿ��:bool<br>true:���� ����<br>false:���� �������� ���� �߻�|
|false�� ������ ����|1. ���� ��ο� ������ ����.|
||2. FileIOManager�� WriteTextToFile()�Լ��� ����.|
||2-1. ��Ʈ���� ������ �ʾҴ�.|
||2-2. ������ ����.|
||2-3. ��Ʈ���� ������ �߻��ߴ�.|

</details>

## �뵵 �� ���

JSON�� �Ľ��ϰ� JSONTree�� �����ϰų�, JSON�� ���Ͽ� �����ϱ� ���� ȣ���ϰ� �����ؾ��ϴ� ���� �Լ��� ��������<br>����ڰ� �Ű澲�� �ʾƵ� �ǵ��� ���ִ°��� �뵵�Դϴ�.

����� JSONParser�� �ν��Ͻ��� �����ϰ�, �ʿ��� �Լ��� ȣ���ϸ� �˴ϴ�.

### ����

```json
{
    "asdf": "value"
}
```

```cpp

//�ʿ��� ������ ����
JSONParser parser;
RootNode root;

std::cout << parser.BuildJSONTreeFromFile(".\\testingFiles\\test.json", root) << '\n';//���Ͽ��� json�����͸� �о�� root�� JSONTree�� �����Ѵ�
//��� : 1

std::cout << root["asdf"].AsString() << '\n';//��� : 

root["asdf"] = "hello, json";//Ű asdf�� ���� hello, json���� ����

std::cout << parser.SaveJSONTreeToFile(".\\testingFiles\\test.json", root) << '\n';//JSONTree�� ����ȭ�� json���Ͽ� ����
//��� : 1

```

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)