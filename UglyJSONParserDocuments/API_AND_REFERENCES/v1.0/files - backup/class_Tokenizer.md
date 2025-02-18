# Tokenizer (class)

### ���:

���ڿ��� ��ūȭ���ִ� ����� ����ϴ� Ŭ����

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/Tokenizer/Tokenizer.hpp

### ����:

UglyJSONParser���� JSONTree�� �����ϱ� ���� �ʿ��� ��ū�� �����ϴ� ������ ����մϴ�.

�̸� �����ϴ� ���� �Լ����� private����� ����ǰ�, Tokenizr()�Լ����� ���˴ϴ�.

�׸���, ��ūȭ �������� ������ �Բ� �����մϴ�.

�̷��� Ư¡������, UglyJSONParser�� �ٸ� �κп����� ������ ���� ���� ����� �����մϴ�.

## �����:

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

||Tokenizer()|
|-|-|
|Ư¡|�⺻ ������|

||Tokenizer(const Tokenizer&)|
|-|-|
|Ư¡|�⺻ ���������|

||Tokenizer(Tokenizer&&)|
|-|-|
|Ư¡|�⺻ �̵�������|

||~Tokenizer()|
|-|-|
|Ư¡|�⺻ �Ҹ���|

</details>

### ����Լ�

<details>
<summary>��ġ��/����</summary>

||Tokenize()|
|-|-|
|����|bool Tokenize(const string& sourceString, std::list\<string\>& outTokenizedStrings);|
|����|�־��� ���ڿ��� ��ūȭ��, ����Ʈ�� �ִ´�. ���� ��ūȭ�� �����ϸ� ����Ʈ�� ����.<br>������ ������ ��� ��ȯ|
|�Ű����� 1|Ÿ��:const std::string&<br>��ūȭ�� ���ڿ�|
|�Ű����� 2|Ÿ��:std::list\<std::string\>&<br>��ūȭ�� ��ū���� ���� ����Ʈ|
|��ȯ|Ÿ��:bool<br>true:��ūȭ ����<br>false:��ūȭ ����|
|false�� ��ȯ�Ǵ� ���:|1:�Էµ� ���ڿ��� ��ūȭ �ϴ� ��������, �ùٸ��� ���� ������ �ִٴ°� ����|

</details>

## �뵵 �� ���

UglyJSONParser���� JSONTree�� �����ϱ� ���� �ʿ��� ��ū�� ���ڿ��κ��� �����ϱ� ���� ���˴ϴ�.

�� Ŭ������ UglyJSONParser���ο��� ���˴ϴ�.

����, �� Ŭ������ ���� ����� ���� ������ JSONParser Ŭ������ �����ξ����ϴ�.

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
Tokenizer tokenizer;
std::string str;
std::list<std::string> tokens;

mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json");//json������ �ε��Ѵ�.

std::cout << tokenizer.Tokenize(str, tokens) << '\n';//���ڿ��� ��ūȭ�Ѵ�.
//��� : 1

for (auto i : tokens)
{
    std::cout << i << '\n';
}
/*
��� : 
{
"asdf"
:
"value"
}
*/
```

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)