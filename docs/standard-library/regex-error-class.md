---
title: regex_error – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: f8f3c88c1b203ed7fcea148843fa99590e27b888
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331872"
---
# <a name="regex_error-class"></a>regex_error – třída

Nahlásí špatný basic_regex objekt.

## <a name="syntax"></a>Syntaxe

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Poznámky

Třída popisuje objekt výjimky, který je vyvolán k hlášení `basic_regex` chyby v konstrukci nebo použití objektu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_error](#regex_error)|Vytvoří objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Kód](#code)|Vrátí kód chyby.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

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

## <a name="regex_errorcode"></a><a name="code"></a>regex_error::kód

Vrátí kód chyby.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která byla předána konstruktoru objektu.

## <a name="regex_errorregex_error"></a><a name="regex_error"></a>regex_error::regex_error

Vytvoří objekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parametry

*Chyba*\
Kód chyby

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, který obsahuje *chybu*hodnoty .

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[třída regex_traits](../standard-library/regex-traits-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)
