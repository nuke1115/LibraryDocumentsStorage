# FileIOManager (class)

### 요약:

텍스트 파일의 입출력을 관리해주는 클래스

### 정의된 파일 및 위치:

Include/UglyJSONParser/FileIO/FileIOManager.hpp

### 설명:

UglyJSONParser에서 텍스트 파일을 읽고 쓸때 사용하는 클래스 입니다.

이를 위해 기본적인 기능들(파일 입/출력, 파일 초기화, 파일이 있는지 확인,생성)을 제공합니다.

## 멤버들:

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

||FileIOManager()|
|-|-|
|특징|기본 생성자|

||FileIOManager(const FileIOManager&)|
|-|-|
|특징|삭제된 함수|

||FileIOManager(FileIOManager&&)|
|-|-|
|특징|삭제된 함수|

||~FileIOManager()|
|-|-|
|특징|기본 소멸자|

</details>

### 멤버함수


<details>
<summary>펼치기/접기</summary>

||IsFileExist()|
|-|-|
|정의|inline bool IsFileExist(const string& filePath)|
|설명|주어진 파일 경로에 파일이 있는지 검사한 후, 결과를 반환합니다.|
|매개변수|타입: const std::string&<br>파일 경로|
|반환|타입:bool<br>true:있다<br>false:없다|

||LoadTextFromFile()|
|-|-|
|정의|bool LoadTextFromFile(string& destination, const string& filePath);|
|설명|주어진 파일 경로로 접근하여, destination 문자열에 파일의 내용을 저장합니다.|
|매개변수 1|타입:std::string&<br>파일의 내용이 저장될 문자열|
|매개변수 2|타입:const std::string&<br>파일의 경로|
|반환|타입:bool<br>true:파일 읽기 성공<br>false:문제 발생|
|반환이 false인 조건|1. filePath가 존제하지 않거나 비어있다.|
||2. ifstream이 열리지 않았다.|

||ClearFile()|
|-|-|
|정의|bool ClearFile(const string& filePath);|
|설명|주어진 파일 경로로 접근하여, 파일의 내용을 삭제합니다.|
|매개변수 |타입:const std::string&<br>파일의 경로|
|반환|타입:bool<br>true:파일 내용 삭제 성공<br>false:문제 발생|
|반환이 false인 조건|1. filePath가 존제하지 않거나 비어있다.|
||2. 스트림에 오류 발생|

||WriteTextToFile()|
|-|-|
|정의|bool WriteTextToFile(const string& data, const string& filePath, std\:\:ios\:\:openmode openMode = std\:\:ios\:\:out \| std\:\:ios\:\:trunc);|
|설명|주어진 파일 경로로 접근하여, 주어진 openMode로 파일을 열고, 주어진 내용을 저장한다.|
|매개변수 1|타입:const std::string&<br>파일에 저장될 문자열|
|매개변수 2|타입:const std::string&<br>파일의 경로|
|매개변수 3|타입:std\:\:ios\:\:openmode<br>파일을 여는 모드<br>기본값:출력모드하고 파일 내용을 덮어쓰는 모드의 혼합|
|반환|타입:bool<br>true:파일 저장 성공<br>false:문제 발생|
|반환이 false인 조건|1. filePath가 존제하지 않거나 비어있다.|
||2. 스트림이 열리지 않았다|
||3. 스트림에 오류 발생|

||CreateFile()|
|-|-|
|오버로드 1|bool CreateFile(const string& filePath, const string& fileName, const string& fileExtension);|
|설명|주어진 문자열들을 합쳐 fullFilePath를 받는 CreateFile오버로드 호출|
|매개변수 1|타입:const std::string&<br>파일이 있을 폴더 경로|
|매개변수 2|타입:const std::string&<br>파일의 이름|
|매개변수 3|타입:const std::string&<br>파일의 확장자|
|반환|타입:bool<br>true:파일 생성 성공<br>false:문제 발생|
|반환이 false인 조건|1. filePath에 매개변수로 받은 파일 이름과 확장자가 동일한 파일이 존제한다.|
||2. 스트림에 오류 발생|
|<span style="color:red">주의</span>|매개변수 1은 반드시 (\\) 문자로 끝나야합니다.|
||매개변수 1은 반드시 존재하는 폴더 및 경로여야 합니다.|
||매개변수 3은 반드시 (.)문자로 시작해야합니다.|

||CreateFile()|
|-|-|
|오버로드 2|bool CreateFile(const string& fullFilePath);|
|설명|주어진 경로에 파일을 생성|
|매개변수|타입:const std::string&<br>파일의 경로, 파일의 이름, 파일의 확장자가 모두 포함된 경로|
|반환|타입:bool<br>true:파일 생성 성공<br>false:문제 발생|
|반환이 false인 조건|1.  filePath에 매개변수로 받은 파일 이름과 동일한 확장자가 파일이 존제한다.|
||2. 스트림에 오류 발생|
|<span style="color:red">주의</span>|매개변수는 반드시 존재하는 폴더 및 경로여야 합니다.|

</details>

## 용도 및 사용

FileIOManager는 파일 입출력과 관련된 기능이 필요할 때 주로 사용합니다.

### 예시

```cpp
//FileIOManager 인스턴스화
FileIOManager mgr;

//필요 변수 선언
std::string str;

//파일 읽기
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json") << '\n';//출력 : 1
std::cout << str << '\n';
/*
출력 :
{
"asdf": "value"
}
*/

//파일 생성 및 파일의 존재 확인 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test.txt") << '\n';//출력 : 0
std::cout << mgr.CreateFile(".\\testingFiles\\test.txt") << '\n';//출력 : 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test.txt") << '\n';//출력 : 1

//파일 생성 및 파일의 존재 확인 2
std::cout << mgr.IsFileExist(".\\testingFiles\\test2.txt") << '\n';//출력 : 0
std::cout << mgr.CreateFile(".\\testingFiles\\","test2",".txt") << '\n';//출력 : 1
std::cout << mgr.IsFileExist(".\\testingFiles\\test2.txt") << '\n';//출력 : 1

//파일에 쓰기
std::cout << mgr.WriteTextToFile("test data", ".\\testingFiles\\test2.txt") << '\n';//출력 : 1
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//출력 : 1
std::cout << str << '\n';//출력 : test data


//파일 내용 삭제
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//출력 : 1
std::cout << str << '\n';//출력 : test data
std::cout << mgr.ClearFile(".\\testingFiles\\test2.txt") << '\n';//출력 : 1
str.clear();
std::cout << mgr.LoadTextFromFile(str, ".\\testingFiles\\test2.txt") << '\n';//출력 : 1
std::cout << str << '\n';//출력 : 


```

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)