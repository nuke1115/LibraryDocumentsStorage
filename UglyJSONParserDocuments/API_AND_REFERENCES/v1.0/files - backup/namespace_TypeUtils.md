# TypeUtils (namespace)

### ���

Ÿ�԰� ���õ� ��ƿ��Ƽ �Լ����� ���ִ� ���ӽ����̽�

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/Utils/TypeUtils.hpp

### ����:

UglyJSONParser ���̺귯������ ����ϴ� Ÿ�԰� ���õ� ��ƿ��Ƽ �Լ����� ���ֽ��ϴ�.

����, ����ڵ� ��� ����������, ���̺귯������ �ʿ��� ���׿� �°Ը� ����� �����Ǿ��ֽ��ϴ�.

����, �׷��� ���������� �ʽ��ϴ�.

### �Լ���:

||ConvertStringToBool()|
|-|-|
|����|inline bool ConvertStringToBool(const std::string& data)|
|����|string Ÿ���� �Ű������� bool�� ��ȯ�� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�Է��� ��ūȭ�� ��ģ ���ڿ��̶�� �����մϴ�.|
|�Ű�����|const std::string&<br>bool�� �ٲ� ���ڿ�|
|��ȯ|Ÿ��:bool<br>true:�Ű������� (true)�� ������<br>false:�Ű������� (true)�� �ƴҶ�|

||ConvertBoolToString()|
|-|-|
|����|std::string ConvertBoolToString(bool data);|
|����|boolŸ���� �Ű������� string���� ��ȯ�� ��ȯ�մϴ�.|
|�Ű�����|Ÿ��:bool<br>���ڿ��� �ٲ� bool|
|��ȯ|Ÿ��:std::string<br>(true):�Ű������� true�϶�<br>(false):�Ű������� false�϶�|

||IsItJsonBool()|
|-|-|
|����|inline bool IsItJsonBool(const std::string& key)|
|����|�Է����� ���� ���ڿ��� json�� bool�� ������ �˻��� ����� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�Է��� ��ūȭ�� ��ģ ���ڿ��̶�� �����մϴ�.|
|�Ű�����|Ÿ��:const std::string&<br>�˻��� ���ڿ�|
|��ȯ|Ÿ��:bool<br>true:���ڿ��� (true) �Ǵ� (false)�϶�<br>false:���ڿ��� (true)(false)�� �� �ƴҶ�|

||IsItJsonString()|
|-|-|
|����|inline bool IsItJsonString(const std::string& key)|
|����|�Ű������� ���� ���ڿ��� �� ���� (")�� �ִ��� �˻��� ��, ����� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�Է��� ��ūȭ�� ��ģ ���ڿ��̶�� �����մϴ�.|
|�Ű�����|Ÿ��const std::string&<br>�˻��� ���ڿ�|
|��ȯ|Ÿ��:bool<br>true:������<br>false:������|

||IsItSingleJsonValue()|
|-|-|
|����|inline bool IsItSingleJsonValue(const std::string& key)|
|����|�Ű������� ���� ���ڿ��� json�� null,bool,number,string ���� �˻��� ��, ����� ��ȯ�մϴ�.|
|<span style="color:red">����</span>|�Է��� ��ūȭ�� ��ģ ���ڿ��̶�� �����մϴ�.|
|�Ű�����|Ÿ��:const std::string&<br>�˻��� ���ڿ�|
|��ȯ|Ÿ��:bool<br>true:������<br>false:�ƴҶ�|

||GetNodeTypeOfToken()|
|-|-|
|����|NodeType GetNodeTypeOfToken(const std::string& token);|
|����|�Է¹��� ���ڿ��� �˻��Ͽ�, ���ڿ� Ÿ�԰� ��ġ�ϴ� ����� Ÿ���� ��ȯ�մϴ�.|
|�Ű�����|Ÿ��:const std::string&<br>�˻��� ���ڿ�|
|��ȯ|Ÿ��:UglyJSONParser::NodeType<br>���� ��ū�� �ش��ϴ� ����� Ÿ��|

## �뵵

�� �Լ����� UglyJSONParser ���̺귯�� ���ο��� �Ľ�, JSONTree ���尰�� �۾����� Ÿ�԰� ���õ� �۾��� �ϱ� ���ؼ� ����������ϴ�.

����, ����� ����������, �Ϲ����� ��Ȳ������ ����� ���� �����ϴ�.

## <span style="color:red">����</span>

�� ���ӽ����̽��� �Լ����� ���ڷ� �޴� ���ڿ�����, **��� ��ūȭ�� ���������� ��ģ ���ڿ�**�̶�� ���� �Ͽ� �ۼ��Ǿ����ϴ�.

�߸��� json������ ���ڿ��� �Էµɽ�, �������� �۵��� ������ �� �����ϴ�.

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)