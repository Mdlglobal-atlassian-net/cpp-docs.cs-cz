---
title: Rozsahy datového typu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04c809249bbe7513e5a1e439ebaf5e4e44a2f758
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418390"
---
# <a name="data-type-ranges"></a>Rozsahy datového typu
Kompilátory jazyka Visual C++ 32bitové a 64bitové verze rozpoznat typy v tabulce dál v tomto článku.  
  
-   `int` (`unsigned int`)  
  
-   `__int8` (`unsigned __int8`)  
  
-   `__int16` (`unsigned __int16`)  
  
-   `__int32` (`unsigned __int32`)  
  
-   `__int64` (`unsigned __int64`)  
  
-   `short` (`unsigned short`)  
  
-   `long` (`unsigned long`)  
  
-   `long` `long` (`unsigned long long`)  
  
 Pokud je jeho název začíná na dvě podtržítka (`__`), datový typ je nestandardní.  
  
 Rozsahy, které jsou určené v následující tabulce jsou inkluzivně inkluzivní.  
  
|Název typu|Bajty|Jiné názvy|Hodnoty rozsahu|  
|---------------|-----------|-----------------|---------------------|  
|int|4|podepsaná|-2 147 483 648 na 2 147 483 647|  
|unsigned int|4|nepodepsaná|0 do 4 294 967 295|  
|__int8|1|char|-128 až 127|  
|__int8 bez znaménka|1|unsigned char|0 až 255|  
|__int16|2|krátký, krátké int, podepsané krátká celočíselná|-32 768 do 32 767|  
|__int16 bez znaménka|2|krátká celočíselná nepodepsané krátké bez znaménka|0 až 65 535|  
|__int32|4|podepsaná, podepsaný int, int|-2 147 483 648 na 2 147 483 647|  
|__int32 bez znaménka|4|int nepodepsané bez znaménka|0 do 4 294 967 295|  
|__int64|8|Long long long long podepsané|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|  
|__int64 bez znaménka|8|long long bez znaménka|0 – 18,446,744,073,709,551,615|  
|bool|1|žádná|false nebo hodnotu true|  
|char|1|žádná|-128 až 127 ve výchozím nastavení<br /><br /> 0 až 255 při kompilaci pomocí [/J](../build/reference/j-default-char-type-is-unsigned.md)|  
|podepsaný char|1|žádná|-128 až 127|  
|unsigned char|1|žádná|0 až 255|  
|short|2|krátká celočíselná, podepsaný krátká celočíselná|-32 768 do 32 767|  
|unsigned short|2|unsigned short int|0 až 65 535|  
|long|4|dlouhé int, int podepsaný dlouho|-2 147 483 648 na 2 147 483 647|  
|unsigned long|4|unsigned long int|0 do 4 294 967 295|  
|long long|8|žádný (ale ekvivalentní __int64)|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|  
|long long bez znaménka|8|žádný (ale ekvivalentní na nepodepsané __int64)|0 – 18,446,744,073,709,551,615|  
|enum|Je to různé.|žádná| |  
|float|4|žádná|3.4e +/-38 (7 míst)|  
|double|8|žádná|1, 7E +/-308 (15 číslic)|  
|long double|Stejné jako datový typ double|žádná|Stejné jako datový typ double|  
|wchar_t|2|__wchar_t|0 až 65 535|  
  
 V závislosti na tom, jak se používá, proměnná `__wchar_t` označí celou – znak typu nebo typ vícebajtových znaků. Použití `L` předpony před znak nebo string konstanta k určení konstanta celou typy znaků.  
  
 `signed` a `unsigned` jsou modifikátory, které můžete použít s žádným typem integrální kromě `bool`. Všimněte si, že `char`, `signed char`, a `unsigned char` jsou tři odlišné typy pro účely mechanismy jako přetížení a šablony.  
  
 `int` a `unsigned int` typy mají velikost čtyři bajtů. Ale nesmí přenosné kódu závisí na velikosti `int` protože jazyk standardní umožňuje, aby to závisí na implementaci.  
  
 C/C++ v sadě Visual Studio také podporuje typy integer s nastavenou velikostí. Další informace najdete v tématu [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) a [omezení typu Integer](../cpp/integer-limits.md).  
  
 Další informace o omezení velikosti jednotlivých typů najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).  
  
 Rozsah výčtových typů se liší v závislosti na kontextu jazyk a zadat příznaky kompilátoru. Další informace najdete v tématu [deklarace výčtů C](../c-language/c-enumeration-declarations.md) a [výčty](../cpp/enumerations-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Základní typy](../cpp/fundamental-types-cpp.md)