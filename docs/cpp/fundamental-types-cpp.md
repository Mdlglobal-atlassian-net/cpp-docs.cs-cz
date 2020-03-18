---
title: Předdefinované typy (C++)
ms.date: 12/11/2019
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
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
ms.openlocfilehash: e67d31e18ebbb6afd9d98542e4a6aa236b2d3e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445307"
---
# <a name="built-in-types-c"></a>Předdefinované typy (C++)

Předdefinované typy (označované také jako *základní typy*) jsou určeny C++ jazykem Standard a jsou integrovány do kompilátoru. Předdefinované typy nejsou definovány v žádném hlavičkovém souboru. Předdefinované typy jsou rozděleny do tří kategorií: integrál, plovoucí desetinná čárka a typ void. Integrální typy jsou schopné zpracovávat celá čísla. Typy s plovoucí desetinnou čárkou umožňují určit hodnoty, které mohou mít zlomkové části.

Typ [void](void-cpp.md) popisuje prázdnou sadu hodnot. Není možné zadat žádnou proměnnou typu **void** – používá se primárně k deklarování funkcí, které nevracejí žádné hodnoty, nebo k deklaraci obecných ukazatelů na netypové nebo libovolně typové údaje. Libovolný výraz může být explicitně převeden nebo převeden na typ **void**. Tyto výrazy jsou však omezeny na následující použití:

- Příkaz výrazu. (Další informace najdete v tématu [výrazy](expressions-cpp.md).)

- Levý operand operátoru čárky (Další informace naleznete v tématu [operátor čárka](comma-operator.md).)

- Druhý nebo třetí operand podmíněného operátoru (`? :`). (Další informace naleznete v tématu [výrazy s podmíněným operátorem](conditional-operator-q.md).)

Následující tabulka vysvětluje omezení velikosti typů ve vztahu k sobě navzájem. Tato omezení platí C++ Standard a jsou nezávislá na implementaci Microsoftu. Absolutní velikost některých předdefinovaných typů není v standardu určena.

### <a name="built-in-type-size-restrictions"></a>Vestavěná omezení velikosti typu

|Kategorie|Typ|Obsah|
|--------------|----------|--------------|
|Integrální|**char**|Typ **char** je integrální typ, který obvykle obsahuje členy základní znakové sady pro spuštění – ve výchozím nastavení je to ASCII v Microsoftu C++.<br /><br /> C++ Kompilátor zpracovává proměnné typu **char**, **signed char**a **unsigned char** s různými typy. Proměnné typu **char** jsou povýšeny na **int** , jako by byly typu **signed char** ve výchozím nastavení, pokud se nepoužije možnost kompilace/j. V tomto případě se považují za typ **char bez znaménka** a jsou povýšeny na **int** bez přípony Sign.|
||**bool**|Typ **bool** je celočíselný typ, který může mít jednu ze dvou hodnot **true** nebo **false**. Jeho velikost není specifikována.|
||**short**|Typ **short int** (nebo jen **krátká**) je celočíselný typ, který je větší nebo roven velikosti typu **char**a menší nebo roven velikosti typu **int**.<br /><br /> Objekty typu **short** lze deklarovat jako **signed short** nebo **unsigned short**. **Signed short** je synonymum pro **krátké**.|
||**int**|Typ **int** je celočíselný typ, který je větší nebo roven velikosti typu **short int**a menší nebo roven velikosti typu **Long**.<br /><br /> Objekty typu **int** lze deklarovat jako **signed int** nebo **unsigned int**. **Signed int** je synonymem pro **int**.|
||**__int8**, **__int16**, **__int32** **__int64**|Size Integer `__int n`, kde `n` je velikost proměnné Integer v bitech. **__int8**, **__int16**, **__int32** a **__Int64** jsou klíčová slova specifická pro společnost Microsoft. Ne všechny typy jsou k dispozici ve všech architekturách. ( **__int128** se nepodporuje.)|
||**long**|Typ **Long** (nebo **Long int**) je celočíselný typ, který je větší nebo roven velikosti typu **int**. (Ve Windows **Long** má stejnou velikost jako **int**.)<br /><br /> Objekty typu **Long** lze deklarovat jako **signed Long** nebo **unsigned long**. **Long signed** je synonymum pro **Long**.|
||**Long Long**|Větší než unsigned **Long**.<br /><br /> Objekty typu **Long Long** lze deklarovat jako **signed** longed Long nebo **unsigned long long**. Long Long **signed Long** je synonymum pro **dlouhou**dobu.|
||**wchar_t** **__wchar_t**|Proměnná typu **wchar_t** určuje typ znaku s velkým znakem nebo vícebajtovým znakem. Ve výchozím nastavení je **wchar_t** nativním typem, ale můžete použít parametr [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) k provedení **wchar_t** definice typu pro **znaménko short**. Typ **__wchar_t** je synonymum specifické pro společnost Microsoft pro nativní typ **wchar_t** .<br /><br /> Použijte předponu L před znakovým nebo řetězcovým literálem k určení typu s velkým znakem.|
|Číslo s plovoucí desetinnou čárkou|**float**|Typ **float** je nejmenší typ s plovoucí desetinnou čárkou.|
||**double**|Typ **Double** je typ s plovoucí desetinnou čárkou, který je větší než nebo roven typu **float**, ale kratší nebo rovno velikosti typu **Long Double**.<br /><br /> Specifické pro společnost Microsoft: reprezentace **Long Double** a **Double** je shodná. **Long Double** a **Double** jsou však samostatné typy.|
||**Long Double**|Typ **Long Double** je typ s plovoucí desetinnou čárkou, který je větší nebo roven typu **Double**.|

**Specifické pro společnost Microsoft**

V následující tabulce je uvedeno množství úložiště potřebné pro předdefinované typy v Microsoftu C++. Zejména Pamatujte, že **dlouhá** je 4 bajty i v 64 operačních systémech.

### <a name="sizes-of-built-in-types"></a>Velikosti předdefinovaných typů

|Typ|Velikost|
|----------|----------|
|**bool**, **char**, **unsigned char**, **signed char**, **__int8**|1 bajt|
|**__int16**, **short**, **unsigned short**, **wchar_t**, **__wchar_t**|2 bajty|
|**float**, **__int32**, **int**, **unsigned int**, **Long**, **unsigned long**|4 bajty|
|**Dvojitá**, **__int64**, **dlouhá dvojitá**, **dlouhá dlouhá**|8 bajtů|

**Specifické pro konec Microsoftu**

V části rozsahy [datových typů](data-type-ranges.md) můžete zobrazit souhrn rozsahu hodnot každého typu.

Další informace o převodu typů naleznete v tématu [standardní převody](standard-conversions.md).

## <a name="see-also"></a>Viz také

[Rozsahy datových typů](data-type-ranges.md)