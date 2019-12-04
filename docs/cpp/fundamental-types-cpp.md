---
title: Základní typy (C++)
ms.date: 11/04/2016
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
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: 99c30eeb942eb3ab57518cc63ce353cfeff0bec9
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810553"
---
# <a name="fundamental-types--c"></a>Základní typy (C++)

Základní typy v C++ jsou rozděleny do tří kategorií: integrál, plovoucí desetinná čárka a typ void. Integrální typy jsou schopné zpracovat celá čísla. Typy s plovoucí desetinnou čárkou umožňují určit hodnoty, které mohou mít zlomkové části.

Typ [void](../cpp/void-cpp.md) popisuje prázdnou sadu hodnot. Není možné zadat žádnou proměnnou typu **void** – používá se primárně k deklarování funkcí, které nevracejí žádné hodnoty, nebo k deklaraci obecných ukazatelů na netypové nebo libovolně typové údaje. Libovolný výraz může být explicitně převeden nebo převeden na typ **void**. Tyto výrazy jsou však omezeny na následující použití:

- Příkaz výrazu. (Další informace naleznete v tématu [výrazy](../cpp/expressions-cpp.md).)

- Levý operand operátoru čárky. (Další informace najdete v tématu [operátor čárky](../cpp/comma-operator.md) .)

- Druhý nebo třetí operand podmíněného operátoru (`? :`). (Další informace naleznete v tématu [výrazy s podmíněným operátorem](../cpp/conditional-operator-q.md) .)

Následující tabulka popisuje omezení velikostí písma. Tato omezení jsou nezávislé implementace společnosti Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Základní typy jazyka C++

|Kategorie|Type|Obsah|
|--------------|----------|--------------|
|Integrál|**char**|Typ **char** je integrální typ, který obvykle obsahuje členy základní znakové sady pro spuštění – ve výchozím nastavení je to ASCII v Microsoftu C++.<br /><br /> C++ Kompilátor zpracovává proměnné typu **char**, **signed char**a **unsigned char** s různými typy. Proměnné typu **char** jsou povýšeny na **int** , jako by byly typu **signed char** ve výchozím nastavení, pokud se nepoužije možnost kompilace/j. V tomto případě se považují za typ **char bez znaménka** a jsou povýšeny na **int** bez přípony Sign.|
||**bool**|Typ **bool** je celočíselný typ, který může mít jednu ze dvou hodnot **true** nebo **false**. Velikost není zadána.|
||**short**|Typ **short int** (nebo jen **krátká**) je celočíselný typ, který je větší nebo roven velikosti typu **char**a menší nebo roven velikosti typu **int**.<br /><br /> Objekty typu **short** lze deklarovat jako **signed short** nebo **unsigned short**. **Signed short** je synonymum pro **krátké**.|
||**int**|Typ **int** je celočíselný typ, který je větší nebo roven velikosti typu **short int**a menší nebo roven velikosti typu **Long**.<br /><br /> Objekty typu **int** lze deklarovat jako **signed int** nebo **unsigned int**. **Signed int** je synonymem pro **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|Size Integer `__int n`, kde `n` je velikost proměnné Integer v bitech. **__int8**, **__int16**, **__int32** a **__Int64** jsou klíčová slova specifická pro společnost Microsoft. Ne všechny typy jsou k dispozici ve všech architekturách. ( **__int128** se nepodporuje.)|
||**long**|Typ **Long** (nebo **Long int**) je celočíselný typ, který je větší nebo roven velikosti typu **int**. (Ve Windows **Long** má stejnou velikost jako **int**.)<br /><br /> Objekty typu **Long** lze deklarovat jako **signed Long** nebo **unsigned long**. **Long signed** je synonymum pro **Long**.|
||**Long Long**|Větší než unsigned **Long**.<br /><br /> Objekty typu **long long** lze deklarovat jako **podepsáno long long** nebo **unsigned long long**. Long Long **signed Long** je synonymum pro **dlouhou**dobu.|
||**wchar_t**, **__wchar_t**|Proměnná typu **wchar_t** určuje typ znaku s velkým znakem nebo vícebajtovým znakem. Ve výchozím nastavení je **wchar_t** nativním typem, ale můžete použít parametr [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) k provedení **wchar_t** definice typu pro **znaménko short**. Typ **__wchar_t** je synonymum specifické pro společnost Microsoft pro nativní typ **wchar_t** .<br /><br /> Použijte předponu L před znakovým nebo řetězcovým literálem k určení typu s velkým znakem.|
|Číslo s plovoucí desetinnou čárkou|**float**|Typ **float** je nejmenší typ s plovoucí desetinnou čárkou.|
||**double**|Typ **Double** je typ s plovoucí desetinnou čárkou, který je větší než nebo roven typu **float**, ale kratší nebo rovno velikosti typu **Long Double**.<br /><br /> Specifické pro společnost Microsoft: reprezentace **Long Double** a **Double** je shodná. **Long Double** a **Double** jsou však samostatné typy.|
||**Long Double**|Typ **Long Double** je typ s plovoucí desetinnou čárkou, který je větší nebo roven typu **Double**.|

**Specifické pro společnost Microsoft**

Následující tabulka uvádí velikost úložiště potřebného pro základní typy v jazyce Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Velikosti základních typů

|Type|Velikost|
|----------|----------|
|**bool**, **char**, **unsigned char**, **signed char**, **__int8**|1 bajt|
|**__int16**, **short**, **unsigned short**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **Long**, **unsigned long**|4 bajty|
|**Dvojitá**, **__int64**, **dlouhá dvojitá**, **dlouhá dlouhá**|8 bajtů|

**Specifické pro konec Microsoftu**

V části rozsahy [datových typů](../cpp/data-type-ranges.md) můžete zobrazit souhrn rozsahu hodnot každého typu.

Další informace o převodu typů naleznete v tématu [standardní převody](../cpp/standard-conversions.md).

## <a name="see-also"></a>Viz také:

[Rozsahy datových typů](../cpp/data-type-ranges.md)