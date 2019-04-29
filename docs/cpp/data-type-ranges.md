---
title: Rozsahy datového typu
ms.date: 11/04/2016
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 88fbb128d995338e5976fbb3df939524f3ef8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392229"
---
# <a name="data-type-ranges"></a>Rozsahy datového typu

Visual C++ 32bitové a 64bitové kompilátory rozpoznají typy v tabulce dále v tomto článku.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Pokud jeho jméno začíná dvěma podtržítky (`__`), datový typ je nestandardní.

Rozsahy, které jsou uvedeny v následující tabulce jsou včetně.

|Název typu|B|Další názvy|Rozsah hodnot|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**podepsané**|-2 147 483 648 do 2 147 483 647|
|**unsigned int**|4|**bez znaménka**|0 do 4 294 967 295|
|**__int8**|1|**char**|-128 až 127|
|**__int8 bez znaménka**|1|**unsigned char**|0 až 255|
|**__int16**|2|**krátký**, **krátká celočíselná**, **podepsané krátká celočíselná**|-32 768 do 32 767|
|**__int16 bez znaménka**|2|**unsigned short**, **unsigned short int**|0 až 65 535|
|**__int32**|4|**podepsané**, **znaménkem**, **int**|-2 147 483 648 do 2 147 483 647|
|**__int32 bez znaménka**|4|**bez znaménka**, **int bez znaménka**|0 do 4 294 967 295|
|**__int64**|8|**Long long**, **podepsáno long long**|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|
|**unsigned __int64**|8|**unsigned long long.**|0 na 18,446,744,073,709,551,615|
|**bool**|1|žádná|**false** nebo **true**|
|**char**|1|žádná|-128 až 127 ve výchozím nastavení<br /><br /> 0 až 255 při kompilaci pomocí [/J](../build/reference/j-default-char-type-is-unsigned.md)|
|**podepsané char**|1|žádná|-128 až 127|
|**unsigned char**|1|žádná|0 až 255|
|**short**|2|**krátká celočíselná**, **podepsané krátká celočíselná**|-32 768 do 32 767|
|**short bez znaménka**|2|**unsigned short int**|0 až 65 535|
|**long**|4|**Long int**, **podepsané long int**|-2 147 483 648 do 2 147 483 647|
|**unsigned long**|4|**unsigned long int**|0 do 4 294 967 295|
|**Long long**|8|žádný (ale ekvivalentní k **__int64**)|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|
|**unsigned long long.**|8|žádný (ale ekvivalentní k **unsigned __int64**)|0 na 18,446,744,073,709,551,615|
|**enum**|Se liší|žádná| |
|**float**|4|žádná|3, 4e +/-38 (7 číslic)|
|**double**|8|žádná|1, 7E +/-308 (15 číslic)|
|**typ long double**|stejné jako **double**|žádná|stejné jako **double**|
|**wchar_t**|2|**__wchar_t**|0 až 65 535|

V závislosti na způsobu jejich použití, proměnná **__wchar_t** označuje buď typ širokého znaku nebo typ vícebajtového znaku. Použití `L` předponu před znak nebo řetězec konstanty k označení celého znaku typu konstanty.

**podepsané** a **bez znaménka** jsou modifikátory používané s jakýmkoli integrálním typem s výjimkou **bool**. Všimněte si, že **char**, **podepsané char**, a **unsigned char** jsou tři odlišné typy pro potřeby mechanismů, jako jsou přetížení nebo šablony.

**Int** a **unsigned int** typy mají velikost čtyři bajty. Však přenositelný kód by neměl záviset na velikosti **int** vzhledem k tomu, že standardní jazyk umožňuje být specifický pro implementaci.

C/C++ v sadě Visual Studio podporuje také celočíselné typy s velikostí. Další informace najdete v tématu [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) a [omezení typu Integer](../cpp/integer-limits.md).

Další informace o omezení velikosti jednotlivých typů naleznete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

Rozsah výčtových typů se liší v závislosti na kontextu jazyka a zadaných příznaků kompilátoru. Další informace najdete v tématu [deklarace výčtů v jazyce C](../c-language/c-enumeration-declarations.md) a [výčty](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Základní typy](../cpp/fundamental-types-cpp.md)