---
title: regex_error – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: eed961ea698591935c22fc748ff79583ae636b27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369615"
---
# <a name="regexerror-class"></a>regex_error – třída

Basic_regex – špatný objekt sestavy.

## <a name="syntax"></a>Syntaxe

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Poznámky

Tato třída popisuje objektu výjimky vyvolané oznámit chybu v konstrukci nebo použití `basic_regex` objektu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_error](#regex_error)|Vytvoří objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[code](#code)|Vrátí kód chyby.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

## <a name="example"></a>Příklad

```cpp
// std__regex__regex_error.cpp
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
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
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

## <a name="code"></a>  regex_error::Code

Vrátí kód chyby.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která byla předána do konstruktoru objektu.

## <a name="regex_error"></a>  regex_error::regex_error

Vytvoří objekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Kód chyby

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, který obsahuje hodnotu *chyba*.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
