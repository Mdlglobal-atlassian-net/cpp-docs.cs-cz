---
title: regex_error – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edcba7e378fc6b7f6bf9028778aa2911fa140dd6
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="regexerror-class"></a>regex_error – třída

Sestavy chybný basic_regex objektu.

## <a name="syntax"></a>Syntaxe

```cpp
class regex_error
 : public std::runtime_error {
public:
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;


};
```

## <a name="remarks"></a>Poznámky

Třída popisuje objekt výjimka vyvolána k hlášení chyby při vytváření nebo použití `basic_regex` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Namespace:** – std

## <a name="code"></a>  regex_error::Code

Vrátí kód chyby.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která byla předána do konstruktoru objektu.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_error_code.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }

```

```Output
regex error: unbalanced parentheses
```

## <a name="regex_error"></a>  regex_error::regex_error

Vytvoří objekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

`error` Kód chyby.

### <a name="remarks"></a>Poznámky

V konstruktoru vytvoří objekt, který obsahuje hodnotu `error`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_error_construct.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code()
                 "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }

```

```Output
regex error: unbalanced parentheses
```

## <a name="see-also"></a>Viz také

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
