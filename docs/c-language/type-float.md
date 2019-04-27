---
title: Float – typ
ms.date: 11/04/2016
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
ms.openlocfilehash: 61bfd094801165e0c3e41e5de6fcbfb0c5e59504
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346324"
---
# <a name="type-float"></a>Float – typ

Čísla s plovoucí desetinnou čárkou IEEE (Institute of Electrical and Electronics Engineers) formát. Hodnoty jednoduchou přesnost s plovoucí desetinnou čárkou typu mít 4 bajty, skládající se z bit znaménka, binární exponent překročení 127 8 bitů a mantisy 23 bitů. Mantisa představuje číslo mezi 1.0 a 2.0. Bit nejvyšším mantisa je vždy 1, není uložen v čísle. Tento zápis poskytuje řadu přibližně 3, 4e-38 3, 4e + 38 pro typ float.

Proměnné můžete deklarovat jako float nebo double, v závislosti na potřebách vaší aplikace. Hlavní rozdíly mezi těmito dvěma typy jsou význam, které můžou představovat, úložiště, které potřebují a jejich rozsah. V následující tabulce jsou uvedeny vztah významu a požadavky na úložiště.

### <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou

|Type|Významných číslic|Počet bajtů|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Proměnné s plovoucí desetinnou čárkou jsou reprezentovány mantisa, který obsahuje hodnotu číslo a exponent, který obsahuje řádově číslo.

V následující tabulce jsou uvedeny počet bitů, které jsou přiděleny mantisy a exponentu pro každý typ s plovoucí desetinnou čárkou. Nejvýznamnější bit jakékoli float nebo double je vždy na bit znaménka. Pokud je 1, číslo se považuje za záporné; v opačném případě bude považován za kladné číslo.

### <a name="lengths-of-exponents-and-mantissas"></a>Délky exponenty a mantisy

|Type|Délka exponentu|Délka mantisa|
|----------|---------------------|---------------------|
|float|8 bitů|23 bitů|
|double|11 bits|52 bitů|

Protože exponenty se ukládají v podobě bez znaménka, je exponent tendenční poloviční hodnotou, je to možné. Pro typ float je posun 127; pro typ double je 1023. Můžete vypočítat skutečnou hodnotu exponentu tak, že se hodnota posunu od hodnotu exponentu.

Mantisa se ukládá jako zlomek binární větší než nebo rovno 1 a menší než 2. Pro typy plovoucí desetinnou čárkou a double je implicitní přední 1 mantisa v pozici nejvýznamnější bit, tak mantisy jsou ve skutečnosti 24 a 53 bitů dlouhý v uvedeném pořadí, i když je nejvýznamnější bit nikdy uložené v paměti.

Namísto metody úložiště, jen je popsáno můžete balíček s plovoucí desetinnou čárkou ukládat binárních čísel s plovoucí desetinnou čárkou jako Nenormalizovaná čísla. "Nenormalizovaná čísla" jsou nenulovou hodnotu s plovoucí desetinnou čárkou čísla pomocí vyhrazené exponentu hodnoty, ve kterých je nejvýznamnější bit mantisa je 0. S použitím Nenormalizovaná formátu, je možné rozšířit rozsah čísla s plovoucí desetinnou čárkou za cenu přesnosti. Nelze určit, zda číslo s plovoucí desetinnou čárkou reprezentované v podobě normalizované nebo Nenormalizovaná; balíček s plovoucí desetinnou čárkou určuje reprezentaci. Balíček s plovoucí desetinnou čárkou nikdy používá nenormalizované formulář, není-li exponent bude menší než minimální, která lze znázornit v normalizovaná forma.

V následující tabulce jsou uvedeny minimální a maximální hodnoty, že můžete ukládat v proměnných každého typu s plovoucí desetinnou čárkou. Hodnoty uvedené v této tabulce platí pouze pro normalizované čísel s plovoucí desetinnou čárkou. Nenormalizovaná čísla s plovoucí desetinnou čárkou mít menší hodnotu minimální. Všimněte si, že čísla v 80*x*87 registry jsou vždy reprezentovány v normalizovaná forma 80-bit; čísla může být reprezentován jenom Nenormalizovaná formuláře po uložené v proměnné s plovoucí desetinnou čárkou 32bitové nebo 64bitové (proměnné float – typ a typ long).

### <a name="range-of-floating-point-types"></a>Rozsah typů s plovoucí desetinnou čárkou

|Type|Minimální hodnota|Maximální hodnota|
|----------|-------------------|-------------------|
|float|1.175494351 E - 38|3.402823466 E + 38|
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|

Pokud přesnost je menší než úložiště žádný problém, zvažte použití typu float pro proměnné s plovoucí desetinnou čárkou. Naopak pokud přesnost je nejdůležitější kritérium, použijte typ double.

Proměnné s plovoucí desetinnou čárkou může být povýšen na typ větší význam (z float – typ na typ double). Povýšení často dojde při provedení aritmetické operace na proměnné s plovoucí desetinnou čárkou. Tato aritmetický se vždy provádí v jako vysoce určitý stupeň přesnost jako proměnnou na nejvyšší úrovni přesnosti. Zvažte například následující typ deklarace:

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

V předchozím příkladu je proměnná `f_short` je povýšen na typ double a vynásobený `f_long`; výsledek se zaokrouhlí na typ float před přiřazením k `f_short`.

V následujícím příkladu (která používá deklarace z předchozího příkladu), že se provádí aritmetické operace v přesnost typu float (32bitová verze) v proměnné; Výsledkem je pak povýšen na typ double:

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Viz také:

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
