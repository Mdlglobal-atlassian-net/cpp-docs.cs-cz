---
title: regex_error – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451655"
---
# <a name="regexerror-class"></a>regex_error – třída

Oznamuje chybný objekt basic_regex.

## <a name="syntax"></a>Syntaxe

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Poznámky

Třída popisuje objekt výjimky vyvolaný pro hlášení chyby při konstrukci nebo použití `basic_regex` objektu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_error](#regex_error)|Vytvoří objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[code](#code)|Vrátí kód chyby.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> regulárního výrazu

**Obor názvů:** std

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

## <a name="code"></a>regex_error:: Code

Vrátí kód chyby.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací hodnotu, která byla předána konstruktoru objektu.

## <a name="regex_error"></a>regex_error::regex_error

Vytvoří objekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

*Chyba*\
Kód chyby

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, který obsahuje *chybu*hodnoty.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)\
[regex_constants – třída](../standard-library/regex-constants-class.md)\
[\<regulární funkce >](../standard-library/regex-functions.md)\
[regex_iterator – třída](../standard-library/regex-iterator-class.md)\
[\<operátory > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)\
[regex_traits – třída](../standard-library/regex-traits-class.md)\
[\<Regex > definice typedef](../standard-library/regex-typedefs.md)
