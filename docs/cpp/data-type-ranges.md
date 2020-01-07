---
title: Rozsahy datového typu
ms.date: 05/07/2019
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
ms.openlocfilehash: 43eb5f34bc587e3ce86532c56d393da3e07c1b03
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301558"
---
# <a name="data-type-ranges"></a>Rozsahy datového typu

Kompilátory C++ Microsoft 32-bit a 64 rozpoznávají typy v tabulce dále v tomto článku.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Pokud název začíná dvěma podtržítky (`__`), datový typ je nestandardní.

Rozsahy, které jsou uvedeny v následující tabulce, jsou zahrnuté (včetně).

|Název typu|Přijaté|Jiné názvy|Rozsah hodnot|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**podpisy**|-2 147 483 648 až 2 147 483 647|
|**unsigned int**|4|**celé**|0 až 4 294 967 295|
|**__int8**|1|**char**|-128 až 127|
|**Nepodepsaný __int8**|1|**znak bez znaménka**|0 až 255|
|**__int16**|2|**short**, **short int**, **signed short int**|-32 768 až 32 767|
|**Nepodepsaný __int16**|2|**krátkodobé bez znaménka**, **krátké celé číslo bez znaménka**|0 až 65 535|
|**__int32**|4|**signed**, **signed int**, **int**|-2 147 483 648 až 2 147 483 647|
|**Nepodepsaný __int32**|4|**unsigned**, **unsigned int**|0 až 4 294 967 295|
|**__int64**|8|**Long**Long, **Podepsáno dlouhou dobu**|– 9223372036854775808 na 9 223 372 036 854 775 807|
|**Nepodepsaný __int64**|8|**dlouhý unsigned long**|0 až 18446744073709551615|
|**bool**|1|žádná|**false** nebo **true**|
|**char**|1|žádná|-128 až 127 ve výchozím nastavení<br /><br /> 0 až 255 při kompilování pomocí [/j](../build/reference/j-default-char-type-is-unsigned.md)|
|**signed char**|1|žádná|-128 až 127|
|**znak bez znaménka**|1|žádná|0 až 255|
|**short**|2|**short int**, **signed short int**|-32 768 až 32 767|
|**krátký unsigned**|2|**krátké celé číslo bez znaménka**|0 až 65 535|
|**long**|4|**Long int**, **signed long int**|-2 147 483 648 až 2 147 483 647|
|**unsigned long**|4|**dlouhé celé číslo bez znaménka**|0 až 4 294 967 295|
|**Long Long**|8|žádný (ale ekvivalentní **__int64**)|– 9223372036854775808 na 9 223 372 036 854 775 807|
|**dlouhý unsigned long**|8|žádný (ale ekvivalentní k **nepodepsanému __int64**)|0 až 18446744073709551615|
|**enum**|se liší|žádná| |
|**float**|4|žádná|3.4 e +/-38 (7 číslic)|
|**double**|8|žádná|1.7 e +/-308 (15 číslic)|
|**Long Double**|stejné jako **Double**|žádná|Stejné jako **Double**|
|**wchar_t**|2|**__wchar_t**|0 až 65 535|

V závislosti na tom, jak se používá, proměnná **__wchar_t** určí buď typ s typem vícebajtového znaku, nebo typ vícebajtového znaku. Použijte předponu `L` před znak nebo řetězcovou konstantou pro určení konstanty typu s velkým znakem.

**znaménka** a **znaménka** jsou modifikátory, které lze použít s libovolným integrálním typem s výjimkou **bool**. Všimněte si, že **char**, **signed char**a **unsigned char** jsou tři různé typy pro účely mechanismů, jako jsou přetížení a šablony.

Typy **int** a **unsigned int** mají velikost 4 bajty. Přenosný kód by však neměl záviset na velikosti **int** , protože Standard jazyka umožňuje, aby tato verze byla specifická pro konkrétní implementaci.

C/C++ v aplikaci Visual Studio podporuje také celočíselné typy s velikostí. Další informace najdete v tématu [__int8, \__int16, \_](../cpp/int8-int16-int32-int64.md) _int32 \_a [omezení celého čísla](../cpp/integer-limits.md).

Další informace o omezení velikosti jednotlivých typů naleznete v tématu [vestavěné typy](../cpp/fundamental-types-cpp.md).

Rozsah výčtových typů se liší v závislosti na kontextu jazyka a zadaných příznaků kompilátoru. Další informace naleznete v tématu deklarace a [výčty](../cpp/enumerations-cpp.md) [výčtu jazyka C](../c-language/c-enumeration-declarations.md) .

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Předdefinované typy](../cpp/fundamental-types-cpp.md)