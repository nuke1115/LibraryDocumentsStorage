# FileIOManager (class)

### ���:

�ؽ�Ʈ ������ ������� �������ִ� Ŭ����

### ���ǵ� ���� �� ��ġ:

Include/UglyJSONParser/FileIO/FileIOManager.hpp

### ����:

UglyJSONParser���� �ؽ�Ʈ ������ �а� ���� ����ϴ� Ŭ���� �Դϴ�.

�̸� ���� �⺻���� ��ɵ�(���� ��/���, ���� �ʱ�ȭ, ������ �ִ��� Ȯ��,����)�� �����մϴ�.

## �����:

### ������ �� �Ҹ���

<details>
<summary>��ġ��/����</summary>

||FileIOManager()|
|-|-|
|Ư¡|�⺻ ������|

||FileIOManager(const FileIOManager&)|
|-|-|
|Ư¡|������ �Լ�|

||FileIOManager(FileIOManager&&)|
|-|-|
|Ư¡|������ �Լ�|

||~FileIOManager()|
|-|-|
|Ư¡|�⺻ �Ҹ���|

</details>

### ����Լ�


<details>
<summary>��ġ��/����</summary>

||IsFileExist()|
|-|-|
|����|inline bool IsFileExist(const string& filePath)|
|����|�־��� ���� ��ο� ������ �ִ��� �˻��� ��, ����� ��ȯ�մϴ�.|
|�Ű�����|Ÿ��: const std::string&<br>���� ���|
|��ȯ|Ÿ��:bool<br>true:�ִ�<br>false:����|

||LoadTextFromFile()|
|-|-|
|����|bool LoadTextFromFile(string& destination, const string& filePath);|
|����|�־��� ���� ��η� �����Ͽ�, destination ���ڿ��� ������ ������ �����մϴ�.|
|�Ű����� 1|Ÿ��:std::string&<br>������ ������ ����� ���ڿ�|
|�Ű����� 2|Ÿ��:const std::string&<br>������ ���|
|��ȯ|Ÿ��:bool<br>true:���� �б� ����<br>false:���� �߻�|
|��ȯ�� false�� ����|1. filePath�� �������� �ʰų� ����ִ�.|
||2. ifstream�� ������ �ʾҴ�.|

||ClearFile()|
|-|-|
|����|bool ClearFile(const string& filePath);|
|����|�־��� ���� ��η� �����Ͽ�, ������ ������ �����մϴ�.|
|�Ű����� |Ÿ��:const std::string&<br>������ ���|
|��ȯ|Ÿ��:bool<br>true:���� ���� ���� ����<br>false:���� �߻�|
|��ȯ�� false�� ����|1. filePath�� �������� �ʰų� ����ִ�.|
||2. ��Ʈ���� ���� �߻�|

||WriteTextToFile()|
|-|-|
|����|bool WriteTextToFile(const string& data, const string& filePath, std\:\:ios\:\:openmode openMode = std\:\:ios\:\:out \| std\:\:ios\:\:trunc);|
|����|�־��� ���� ��η� �����Ͽ�, �־��� openMode�� ������ ����, �־��� ������ �����Ѵ�.|
|�Ű����� 1|Ÿ��:const std::string&<br>���Ͽ� ����� ���ڿ�|
|�Ű����� 2|Ÿ��:const std::string&<br>������ ���|
|�Ű����� 3|Ÿ��:std\:\:ios\:\:openmode<br>������ ���� ���<br>�⺻��:��¸���ϰ� ���� ������ ����� ����� ȥ��|
|��ȯ|Ÿ��:bool<br>true:���� ���� ����<br>false:���� �߻�|
|��ȯ�� false�� ����|1. filePath�� �������� �ʰų� ����ִ�.|
||2. ��Ʈ���� ������ �ʾҴ�|
||3. ��Ʈ���� ���� �߻�|

||CreateFile()|
|-|-|
|�����ε� 1|bool CreateFile(const string& filePath, const string& fileName, const string& fileExtension);|
|����|�־��� ���ڿ����� ���� fullFilePath�� �޴� CreateFile�����ε� ȣ��|
|�Ű����� 1|Ÿ��:const std::string&<br>������ ���� ���� ���|
|�Ű����� 2|Ÿ��:const std::string&<br>������ �̸�|
|�Ű����� 3|Ÿ��:const std::string&<br>������ Ȯ����|
|��ȯ|Ÿ��:bool<br>true:���� ���� ����<br>false:���� �߻�|
|��ȯ�� false�� ����|1. filePath�� �Ű������� ���� ���� �̸��� Ȯ���ڰ� ������ ������ �����Ѵ�.|
||2. ��Ʈ���� ���� �߻�|
|<span style="color:red">����</span>|�Ű����� 1�� �ݵ�� (\\) ���ڷ� �������մϴ�.|
||�Ű����� 1�� �ݵ�� �����ϴ� ���� �� ��ο��� �մϴ�.|
||�Ű����� 3�� �ݵ�� (.)���ڷ� �����ؾ��մϴ�.|

||CreateFile()|
|-|-|
|�����ε� 2|bool CreateFile(const string& fullFilePath);|
|����|�־��� ��ο� ������ ����|
|�Ű�����|Ÿ��:const std::string&<br>������ ���, ������ �̸�, ������ Ȯ���ڰ� ��� ���Ե� ���|
|��ȯ|Ÿ��:bool<br>true:���� ���� ����<br>false:���� �߻�|
|��ȯ�� false�� ����|1.  filePath�� �Ű������� ���� ���� �̸��� ������ Ȯ���ڰ� ������ �����Ѵ�.|
||2. ��Ʈ���� ���� �߻�|
|<span style="color:red">����</span>|�Ű������� �ݵ�� �����ϴ� ���� �� ��ο��� �մϴ�.|

</details>

## �뵵 �� ���

FileIOManager�� ���� ����°� ���õ� ����� �ʿ��� �� �ַ� ����մϴ�.

### ����

```cpp
//FileIOManager �ν��Ͻ�ȭ
FileIOManager mgr;

//�ʿ� ���� ����
std::string str;

//���� �б�
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json") << '\n';//��� : 1
std::cout << str << '\n';
/*
��� :
{
"asdf": "value"
}
*/

//���� ���� �� ������ ���� Ȯ�� 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test.txt") << '\n';//��� : 0
std::cout << mgr.CreateFile(".\\testingFiles\\test.txt") << '\n';//��� : 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test.txt") << '\n';//��� : 1

//���� ���� �� ������ ���� Ȯ�� 2
std::cout << mgr.IsFileExist(".\\testingFiles\\test2.txt") << '\n';//��� : 0
std::cout << mgr.CreateFile(".\\testingFiles\\","test2",".txt") << '\n';//��� : 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test2.txt") << '\n';//��� : 1

//���Ͽ� ����
std::cout << mgr.WriteTextToFile("test data", ".\\testingFiles\\test2.txt") << '\n';//��� : 1
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//��� : 1
std::cout << str << '\n';//��� : test data


//���� ���� ����
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//��� : 1
std::cout << str << '\n';//��� : test data
std::cout << mgr.ClearFile(".\\testingFiles\\test2.txt") << '\n';//��� : 1
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//��� : 1
std::cout << str << '\n';//��� : 


```

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)