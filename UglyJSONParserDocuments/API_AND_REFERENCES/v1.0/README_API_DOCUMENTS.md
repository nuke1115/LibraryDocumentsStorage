# UglyJSONParser v1.0 API Document 

## 개요

1. 버전
2. 프로젝트의 구조

---

# 1. 프로젝트의 현제 버전

v1.0

---

# 2. 프로젝트의 구조:

## 1. UglyJSONParser 폴더의 구조

```bash
UglyJSONParser:
├─Include//헤더파일이 모여있는 공간
│  └─UglyJSONParser
│      │  FileIOInclude.hpp
│      │  JSONParserInclude.hpp
│      │  JSONTreeInclude.hpp
│      │  TokenizerInclude.hpp
│      │  UglyJSONParserIncludeHeader.hpp
│      │  UtilsInclude.hpp
│      │
│      ├─FileIO
│      │      FileIOManager.hpp
│      │
│      ├─JSONParser
│      │      JSONParser.hpp
│      │
│      ├─JSONTree
│      │      JSONTreeBuilder.hpp
│      │      Node.hpp
│      │      NodeBase.hpp
│      │      NodeTypes.hpp
│      │
│      ├─Tokenizer
│      │      Tokenizer.hpp
│      │      Tokens.hpp
│      │
│      └─Utils
│              StringUtils.hpp
│              TypeUtils.hpp
│
└─src//헤더파일의 구현파일이 모여있는 공간
   ├─FileIO
   │      FileIOManager.cpp
   │
   ├─JSONParser
   │      JSONParser.cpp
   │
   ├─JSONTree
   │      JSONTreeBuilder.cpp
   │      Node.cpp
   │      NodeBase.cpp
   │
   ├─Tokenizer
   │      Tokenizer.cpp
   │
   └─Utils
           StringUtils.cpp
           TypeUtils.cpp

```


## 2. 프로젝트의 코드 구조
+ [UglyJSONParser (Namespace)](./files/namespace_UglyJSONParser.md)
    + [BaseNode (Base Class)](./files/class_BaseNode.md)
        + [ArrayNode (Class, Derived from BaseNode)](./files/class_ArrayNode.md)
        + [BoolNode (Class, Derived from BaseNode)](./files/class_BoolNode.md)
        + [NullNode (Class, Derived from BaseNode)](./files/class_NullNode.md)
        + [NumberNode (Class, Derived from BaseNode)](./files/class_NumberNode.md)
        + [ObjectNode (Class, Derived from BaseNode)](./files/class_ObjectNode.md)
        + [RootNode (Class, Derived from BaseNode)](./files/class_RootNode.md)
        + [StringNode (Class, Derived from BaseNode)](./files/class_StringNode.md)
    + [FileIOManager (Class)](./files/class_FileIOManager.md)
    + [JSONParser (Class)](./files/class_JSONParser.md)
    + [JSONTreeBuilder (Class)](./files/class_JSONTreeBuilder.md)
    + [NodeFactory (Class)](./files/class_NodeFactory.md)
    + [NodeType (Enum Class)](./files/enum_class_NodeType.md)
    + [StringUtils (Namespace)](./files/namespace_StringUtils.md)
    + [Tokenizer (Class)](./files/class_Tokenizer.md)
    + [Tokens (Namespace)](./files/namespace_Tokens.md)
    + [TypeUtils (Namespace)](./files/namespace_TypeUtils.md)

---

# 돌아가기

[README.md](https://github.com/nuke1115/UglyJSONParser/blob/dev/README.md)
