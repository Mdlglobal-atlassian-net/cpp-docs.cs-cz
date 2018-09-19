---
title: Základní typy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7abb1efa9ca7260648574299cde454a33f84b3f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114888"
---
# <a name="fundamental-types--c"></a>Základní typy (C++)

Základní typy jazyka C++ jsou rozděleny do tří kategorií: integrální plovoucí desetinná čárka a void. Integrální typy jsou schopné zpracovat celá čísla. Typy plovoucího bodu jsou schopny určit hodnoty, které mohou mít zlomkové části.

[Void](../cpp/void-cpp.md) typu popisuje prázdnou sadu hodnot. Žádné proměnné typu **void** je možné zadat – používá se především k deklarování funkcí, které nevrací žádnou hodnotu nebo pro deklaraci obecných ukazatelů na netypový kód nebo s libovolným typem data. Libovolný výraz může být explicitně převeden nebo přetypován na typ **void**. Tyto výrazy jsou však omezeny na následující použití:

- Příkaz výrazu. (Viz [výrazy](../cpp/expressions-cpp.md), další informace.)

- Levý operand operátoru čárky. (Viz [operátor čárky](../cpp/comma-operator.md) Další informace.)

- Druhý nebo třetí operanda podmíněného operátoru (`? :`). (Viz [výrazy s podmíněným operátorem](../cpp/conditional-operator-q.md) Další informace.)

Následující tabulka popisuje omezení velikostí písma. Tato omezení jsou nezávislé implementace společnosti Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Základní typy jazyka C++

|Kategorie|Typ|Obsah|
|--------------|----------|--------------|
|Celočíselný typ|**char**|Typ **char** je integrálový typ, který obvykle obsahuje členy znakové sady spuštění základní – ve výchozím nastavení, je to ASCII v Microsoft C++.<br /><br /> Kompilátor C++ zpracovává proměnné typu **char**, **podepsané char**, a **unsigned char** tak, že má různé typy. Proměnné typu **char** jsou povýšeny do **int** jakoby se jednalo o typ **podepsané char** ve výchozím nastavení, pokud není použita možnost kompilace/j. V tomto případě jsou považovány za typ **unsigned char** a jsou povýšeny do **int** bez přípony sign.|
||**bool**|Typ **bool** je integrálový typ, který může mít jednu ze dvou hodnot **true** nebo **false**. Velikost není zadána.|
||**short**|Typ **krátká celočíselná** (nebo jednoduše **krátký**) je integrálový typ, který je větší než nebo rovno velikosti typu **char**a kratší než nebo rovno velikosti typu **int**.<br /><br /> Objekty typu **krátký** lze deklarovat jako **podepsané řečeno** nebo **unsigned short**. **Podepsané řečeno** je synonymum pro **krátký**.|
||**int**|Typ **int** je integrálový typ, který je větší než nebo rovno velikosti typu **krátká celočíselná**a kratší než nebo rovno velikosti typu **dlouhé**.<br /><br /> Objekty typu **int** lze deklarovat jako **znaménkem** nebo **unsigned int**. **Znaménkem** je synonymum pro **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|Integer s nastavenou velikostí `__int n`, kde `n` velikost, v bitech celočíselné proměnné. **__int8**, **__int16**, **__int32** a **__int64** jsou klíčová slova specifická pro společnost Microsoft. Ne všechny typy jsou k dispozici ve všech architekturách. (**__int128** se nepodporuje.)|
||**long**|Typ **dlouhé** (nebo **long int**) je integrálový typ, který je větší než nebo rovno velikosti typu **int**.<br /><br /> Objekty typu **dlouhé** lze deklarovat jako **podepsané dlouho** nebo **unsigned long**. **Podepsané dlouho** je synonymum pro **dlouhé**.|
||**Long long**|Větší než nepodepsaný **dlouhé**.<br /><br /> Objekty typu **long long** lze deklarovat jako **podepsáno long long** nebo **unsigned long long**. **podepsáno long long** je synonymum pro **long long**.|
||**wchar_t**, **__wchar_t**|Proměnné typu **wchar_t** označuje typ širokého znaku nebo vícebajtového znaku. Ve výchozím nastavení **wchar_t** je nativní typ, ale můžete použít [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) aby **wchar_t** definice typu **unsigned short**. **__Wchar_t** typ je synonymum pro nativní specifické pro společnost Microsoft **wchar_t** typu.<br /><br /> Použijte předponu L před znak nebo textový literál, chcete-li určit typ širokého znaku.|
|Plovoucí desetinná čárka|**float**|Typ **float** je nejmenší plovoucí typu bodu.|
||**double**|Typ **double** je plovoucí typ bodu, který je větší než nebo rovno typu **float**, ale kratší než nebo rovno velikosti typu **long double**.<br /><br /> Specifické pro Microsoft: reprezentace **long double** a **double** je stejný jako. Ale **long double** a **double** jsou zvláštní typy.|
||**typ long double**|Typ **long double** je plovoucí typ bodu, který je větší než nebo rovno typu **double**.|

**Specifické pro Microsoft**

Následující tabulka uvádí velikost úložiště potřebného pro základní typy v Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Velikosti základních typů

|Typ|Velikost|
|----------|----------|
|**BOOL**, **char**, **unsigned char**, **podepsané char**, **__int8**|1 bajt|
|**__int16**, **krátký**, **unsigned short**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **dlouhé**, **unsigned long**|4 bajty|
|**dvojité**, **__int64**, **long double**, **long long**|8 bajtů|

**Specifické pro END Microsoft**

Zobrazit [rozsahy datového typu](../cpp/data-type-ranges.md) souhrnné informace o rozsahu hodnot jednotlivých typů.

Další informace o převodu typů najdete v tématu [standardní převody](../cpp/standard-conversions.md).

## <a name="see-also"></a>Viz také:

[Rozsahy datových typů](../cpp/data-type-ranges.md)