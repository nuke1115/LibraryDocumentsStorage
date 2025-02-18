# Tokenizer (class)

### 요약:

문자열을 토큰화해주는 기능을 담당하는 클래스

### 정의된 파일 및 위치:

Include/UglyJSONParser/Tokenizer/Tokenizer.hpp

### 설명:

UglyJSONParser에서 JSONTree를 빌드하기 위해 필요한 토큰을 생성하는 역할을 담당합니다.

이를 수행하는 여러 함수들이 private멤버로 선언되고, Tokenizr()함수에서 사용됩니다.

그리고, 토큰화 과정에서 검증도 함께 수행합니다.

이런한 특징때문에, UglyJSONParser의 다른 부분에서는 별도의 검증 없이 사용이 가능합니다.

## 멤버들:

### 생성자 및 소멸자

<details>
<summary>펼치기/접기</summary>

||Tokenizer()|
|-|-|
|특징|기본 생성자|

||Tokenizer(const Tokenizer&)|
|-|-|
|특징|기본 복사생성자|

||Tokenizer(Tokenizer&&)|
|-|-|
|특징|기본 이동생성자|

||~Tokenizer()|
|-|-|
|특징|기본 소멸자|

</details>

### 멤버함수

<details>
<summary>펼치기/접기</summary>

||Tokenize()|
|-|-|
|정의|bool Tokenize(const string& sourceString, std::list\<string\>& outTokenizedStrings);|
|설명|주어진 문자열을 토큰화해, 리스트에 넣는다. 만약 토큰화를 실패하면 리스트를 비운다.<br>과정이 끝나면 결과 반환|
|매개변수 1|타입:const std::string&<br>토큰화할 문자열|
|매개변수 2|타입:std::list\<std::string\>&<br>토큰화한 토큰들을 담을 리스트|
|반환|타입:bool<br>true:토큰화 성공<br>false:토큰화 실패|
|false가 반환되는 경우:|1:입력된 문자열을 토큰화 하는 과정에서, 올바르지 않은 문법이 있다는걸 감지|

</details>

## 용도 및 사용

UglyJSONParser에서 JSONTree를 빌드하기 위해 필요한 토큰을 문자열로부터 생성하기 위해 사용됩니다.

이 클래스는 UglyJSONParser내부에서 사용됩니다.

또한, 이 클래스를 직접 사용할 일이 없도록 JSONParser 클래스를 만들어두었습니다.

따라서, 사용자가 이 클래스를 직접 사용할 상황은 거의 없습니다.

### 예시

```json
{
    "asdf": "value"
}
```

```cpp
//필요한 변수들 선언
FileIOManager mgr;
Tokenizer tokenizer;
std::string str;
std::list<std::string> tokens;

mgr.LoadTextFromFile(str, ".\\testingFiles\\test.json");//json파일을 로드한다.

std::cout << tokenizer.Tokenize(str, tokens) << '\n';//문자열을 토큰화한다.
//출력 : 1

for (auto i : tokens)
{
    std::cout << i << '\n';
}
/*
출력 : 
{
"asdf"
:
"value"
}
*/
```

# 돌아가기

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)