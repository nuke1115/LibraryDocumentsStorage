# Tokens (namespace)

### ���

JSON ��ūȭ�� �ʿ��� ������� ���ִ� ���ӽ����̽�

### ���ǵ� ���� �� ��ġ:
Include/UglyJSONParser/Tokenizer/Tokens.hpp

### ����:

���ڿ��� JSONTreeBuilder���� ��� ������ ��ū��� ��ūȭ�� ��, Tokenizer���� ����ϴ� ������� �����Դϴ�. 

## �����

<details>
<summary>��ġ��/����</summary>

|��ū �̸�|����|
|-|-|
|TokenTrue|JSON�� true�� ���ڿ� ��ū���� ��ȯ�Ѱ�|
|TokenFalse|JSON�� false�� ���ڿ� ��ū���� ��ȯ�Ѱ�|
|TokenNull|JSON�� null�� ���ڿ� ��ū���� ��ȯ�Ѱ�|
|TokenQuotationMark|JSON�� ���ڿ��� ���۰� ���� ���δ� (")�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenObjectStart<br>TokenObjectEnd|JSON�� Object�� ���� �ݴ� ���ڸ� ��ū���� ��ȯ�Ѱ�.<br>���°� : ({)<br>�ݴ°� : (})|
|TokenArrayStart<br>TokenArrayEnd|JSON�� Array�� ���� �ݴ� ���ڸ� ��ū���� ��ȯ�Ѱ�.<br>���°� : ([)<br>�ݴ°� : (])|
|TokenComma|��ǥ(,)�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenPlus<br>TokenMinus|��ȣ(+,-)�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenColon|�ݷ�(:)�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenBackslash|�齽����(\) �� ���� ��ū���� ��ȯ�Ѱ�.|
|NumRangeStart<br>NumRangeEnd|ASCIICode������ ���� ������ ����(0)�� ��(9)�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenDecimalPoint|�Ҽ���(.)�� ���� ��ū���� ��ȯ�Ѱ�|
|TokenExponentUpper<br>TokenExponentLower|���� ��ȣ(E,e)�� �빮�ڿ� �ҹ��ڸ� ���� ��ū���� ��ȯ�Ѱ�|
|TokenSpace|�����̽� ���ڸ� ���� ��ū���� ��Ÿ����|
|TokenLineFeed|(\n) �� ���� ��ū���� ��Ÿ����|
|TokenCarriageReturn|(\r)�� ���� ��ū���� ��Ÿ����|
|TokenHorizontalTab|(\t)�� ���� ��ū���� ��Ÿ����|

</details>



## �뵵

�� ������� UglyJSONParser�� Tokenizer���� ����ϱ� ���� ���ǵǾ����ϴ�.

��ũ�������� ����ڰ� �ٽ� �ۼ��Ϸ��� ���� �ʴ��̻�, �� ������� ���� ����� ���� �����ϴ�.

# ���ư���

[UglyJSONParser (namespace)](namespace_UglyJSONParser.md)