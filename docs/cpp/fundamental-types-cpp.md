---
title: "Základní typy (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb52d6a987289ed77d7b63a5497323ddad2b467
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fundamental-types--c"></a>Základní typy (C++)
Základní typy v jazyce C++ jsou rozdělené do tří kategorií: integrální plovoucí bodu a void. Celočíselné typy jsou umožňuje zpracovávat celá čísla. Plovoucí typy bodů jsou schopná využívat zadání hodnoty, které může mít zlomkové části.  
  
 [Void](../cpp/void-cpp.md) typu popisuje prázdnou sadu hodnot. Žádné proměnné typu `void` lze zadat – používá se především k deklarovat funkce, které vrací žádné hodnoty nebo deklarovat obecné ukazatele na netypové nebo nahodile zadané data. Jakýkoli výraz může být explicitně převést nebo přetypovat na typ `void`. Tyto výrazy jsou však omezeny na používá následující:  
  
-   Příkaz výrazu. (Viz [výrazy](../cpp/expressions-cpp.md), další informace.)  
  
-   Levý operand operátoru čárkami. (Viz [operátor čárky](../cpp/comma-operator.md) Další informace.)  
  
-   Druhý a třetí operand operátoru podmíněného (`? :`). (Viz [výrazy s podmíněný operátor](../cpp/conditional-operator-q.md) Další informace.)  
  
 Následující tabulka vysvětluje velikostí typ omezení. Tato omezení jsou nezávislé na implementaci společnosti Microsoft.  
  
### <a name="fundamental-types-of-the-c-language"></a>Základní typy jazyka C++  
  
|Kategorie|Typ|Obsah|  
|--------------|----------|--------------|  
|Celé číslo|`char`|Typ `char` je integrální typ, který obvykle obsahuje členy znaková sada spuštění základní – ve výchozím nastavení, to je ASCII v Microsoft C++.<br /><br /> Kompilátor C++ zpracovává proměnné typu `char`, `signed` `char`, a `unsigned` `char` tak, že má různých typů. Proměnné typu `char` povýšené na `int` jako v případě, že jsou typ `signed` `char` ve výchozím nastavení, pokud se používá možnost /J kompilace. V takovém případě jsou považovány za typ `unsigned` `char` a povýšené na `int` bez přípony přihlášení.|  
||`bool`|Typ `bool` je integrální typ, který může mít jednu ze dvou hodnot `true` nebo `false`. Jeho velikost neurčená.|  
||`short`|Typ `short` `int` (nebo jednoduše `short`) je integrální typ, který je větší než nebo rovna velikosti typu `char`a kratší než nebo rovna velikosti typu `int`.<br /><br /> Objekty typu `short` lze deklarovat jako `signed` `short` nebo `unsigned short`. `Signed short`je synonymum pro `short`.|  
||`int`|Typ `int` je integrální typ, který je větší než nebo rovna velikosti typu `short` `int`a kratší než nebo rovna velikosti typu `long`.<br /><br /> Objekty typu `int` lze deklarovat jako `signed` `int` nebo `unsigned` `int`. `Signed``int` se jedná o synonymum `int`.|  
||`__int8`, `__int16`, `__int32`, `__int64`|Integer s nastavenou velikostí `__int n`, kde `n` je velikost v bitech, proměnné, celé číslo. `__int8`, `__int16`, `__int32` a `__int64` jsou klíčová slova specifická pro společnost Microsoft. Ne všechny typy jsou k dispozici na všech architektury. `(__int128`není podporována.)|  
||`long`|Typ `long` (nebo `long` `int`) je integrální typ, který je větší než nebo rovna velikosti typu `int`.<br /><br /> Objekty typu `long` lze deklarovat jako `signed` `long` nebo `unsigned` `long`. `Signed``long` se jedná o synonymum `long`.|  
||`long``long`|Větší než nepodepsaný `long`.<br /><br /> Objekty typu `long long` lze deklarovat jako `signed` `long long` nebo `unsigned` `long long`. `signed``long long` se jedná o synonymum `long long`.|  
||`wchar_t`, `__wchar_t`|Proměnné typu `wchar_t` označí typu široká charakterová nebo vícebajtových znaků. Ve výchozím nastavení `wchar_t` je nativní typ, ale můžete použít [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) aby `wchar_t` typedef pro `unsigned short`. `__wchar_t` Typ je specifické pro společnost Microsoft synonymum pro nativního `wchar_t` typu.<br /><br /> K určení typu široká charakterová použijte předponu L před znak nebo řetězcový literál.|  
|Plovoucí desetinné čárky|`float`|Typ `float` je nejmenší plovoucí typu bodu.|  
||`double`|Typ `double` plovoucí typ bodu, která je větší než nebo rovno zadejte `float`, ale kratší než nebo rovna velikosti typu `long` `double`.<br /><br /> Microsoft konkrétní: reprezentace `long double` a `double` se shoduje. Ale `long double` a `double` jsou samostatné typy.|  
||`long double`|Typ `long` `double` plovoucí typ bodu, která je větší než nebo rovno zadejte `double`.|  
  
 **Konkrétní Microsoft**  
  
 Následující tabulka uvádí velikost úložiště, které jsou potřeba pro základní typy v Microsoft C++.  
  
### <a name="sizes-of-fundamental-types"></a>Velikost základní typy  
  
|Typ|Velikost|  
|----------|----------|  
|`bool`, `char`, `unsigned char`, `signed char`, `__int8`|1 bajt|  
|`__int16`, `short`, `unsigned short`, `wchar_t`, `__wchar_t`|2 bajtů|  
|`float`, `__int32`, `int`, `unsigned int`, `long`, `unsigned long`|4 bajty|  
|`double`, `__int64`, `long double`, `long long`|8 bajtů|  
  
 **Konkrétní Microsoft END**  
  
 V tématu [rozsahy datového typu](../cpp/data-type-ranges.md) souhrnné informace o rozsahu hodnot každého typu.  
  
 Další informace o převodu typů najdete v tématu [standardní převody](../cpp/standard-conversions.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozsahy datových typů](../cpp/data-type-ranges.md)