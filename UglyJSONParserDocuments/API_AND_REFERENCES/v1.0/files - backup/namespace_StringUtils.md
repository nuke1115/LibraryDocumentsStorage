# StringUtils (namespace)

### ���

���� �Ǵ� ���ڿ��� ���õ� ��ƿ��Ƽ �Լ����� ���ִ� ���ӽ����̽�

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/Utils/StringUtils.hpp

### ����:

UglyJSONParser ���̺귯������ ����ϴ� ���� �Ǵ� ���ڿ��� ���õ� ��ƿ��Ƽ �Լ����� ���ֽ��ϴ�.

����, ����ڵ� ��� ����������, ���̺귯������ �ʿ��� ���׿� �°Ը� ����� �����Ǿ��ֱ⿡, �׷��� ���������� �ʽ��ϴ�.

### �Լ���:


<details>
<summary>��ġ��/����</summary>

||CompareString()|
|-|-|
|����|bool CompareString(const std::string& target, const std::string& key, size_t targetStringStartIndex);|
|����|target���ڿ��� targetStringStartIndex ���� key���ڿ��� ���̿� �ش��ϴ� ������ ���ڿ�,<br>key���ڿ��� ���ۺ��� �������� ���ڵ��� ���ϴ� �Լ�.|
|�Ű����� 1|Ÿ��:const std::string&<br>key�� ������ �˻��� ���(target)|
|�Ű����� 2|Ÿ��:const std::string&<br>key|
|�Ű����� 3|Ÿ��:size_t<br>target���� �񱳸� ������ ���ڿ��� ��ġ�� ����Ű�� �ε���|
|��ȯ|Ÿ��:bool<br>true: �Ű����� 3�� ����Ű�� ������ target ���ڿ��κ��� key�� ���� ����� �����ϴ�.<br>false: �ٸ��ϴ�.|

||IsItDigit()|
|-|-|
|����|inline bool IsItDigit(const char token)|
|����|�Է����� ���� token�� 0~9������ ���� �ȿ� �ִ��� �˻��մϴ�.|
|�Ű�����|Ÿ��:char<br>�˻��� ��ū|
|��ȯ|Ÿ��:bool<br>true:���� �ȿ� �ֽ��ϴ�.<br>false:���� �ȿ� �����ϴ�.|

||IsItOpeningToken()|
|-|-|
|����|inline bool IsItOpeningToken(const char token)|
|����|�Է����� ���� token�� ������ū([,{) ���� �ϳ����� �˻��մϴ�.|
|�Ű�����|Ÿ��:char<br>�˻��� ��ū|
|��ȯ|Ÿ��:bool<br>true:������ū �Դϴ�.<br>false:������ū�� �ƴմϴ�.|

||IsItClosingToken()|
|-|-|
|����|inline bool IsItClosingToken(const char token)|
|����|�Է����� ���� token�� �ݴ���ū(],}) ���� �ϳ����� �˻��մϴ�.|
|�Ű�����|Ÿ��:char<br>�˻��� ��ū|
|��ȯ|Ÿ��:bool<br>true:�ݴ���ū �Դϴ�.<br>false:�ݴ���ū�� �ƴմϴ�.|

||IsItSign()|
|-|-|
|����|inline bool IsItSign(const char token)|
|����|�Է����� ���� token�� ��ȣ(+,-) ���� �ϳ����� �˻��մϴ�.|
|�Ű�����|Ÿ��:char<br>�˻��� ��ū|
|��ȯ|Ÿ��:bool<br>true:��ȣ�Դϴ�.<br>false:��ȣ�� �ƴմϴ�.|

||Contains()|
|-|-|
|����|inline bool Contains(const std::string& source, const char key)|
|����|�Է����� ���� ���ڿ��� �Է����� ���� char�� �����ϴ��� �˻��մϴ�.|
|�Ű����� 1|Ÿ��:const std::string&<br>�˻��� ���ڿ�|
|�Ű����� 2|Ÿ��:char<br>ã�� ��ū|
|��ȯ|Ÿ��:bool<br>true:�����մϴ�.<br>false:�������� �ʽ��ϴ�.|

</details>

## �뵵

�� �Լ����� UglyJSONParser ���̺귯�� ���ο��� �Ľ�, JSONTree ���尰�� �۾����� ���ڿ��� ���õ� ���۾��� �ϱ� ���ؼ� ����������ϴ�.

����, ����� ����������, �Ϲ����� ��Ȳ������ ����� ���� �����ϴ�.

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)