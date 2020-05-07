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

Čísla s plovoucí desetinnou čárkou používají formát IEEE (Institute of Electrical and Electronics Engineers). Hodnoty s jednoduchou přesností s typem float mají 4 bajty, které se skládají z znaku znaménka, 8bitového ne127 binárního exponentu a 23-bit mantisy. Mantisa představuje číslo mezi 1,0 a 2,0. Vzhledem k tomu, že horní bit mantisy je vždy 1, není uložen v čísle. Tato reprezentace poskytuje rozsah přibližně 3.4 E-38 až 3.4 E + 38 pro typ float.

Proměnné můžete deklarovat jako float nebo Double v závislosti na potřebách vaší aplikace. Hlavní rozdíly mezi těmito dvěma typy jsou význam, který mohou představovat, úložiště, které potřebují, a jejich rozsah. V následující tabulce je uveden vztah mezi požadavky na význam a úložiště.

### <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou

|Typ|Významné číslice|Počet bajtů|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Proměnné s plovoucí desetinnou čárkou jsou reprezentovány pomocí mantisy, která obsahuje hodnotu čísla a exponent, který obsahuje pořadí čísla.

Následující tabulka ukazuje počet bitů přiřazených k mantise a exponent pro každý typ s plovoucí desetinnou čárkou. Nejvýznamnější bit libovolného typu float nebo Double je vždy bit znaménka. Pokud je hodnota 1, je číslo považováno za záporné. v opačném případě se považuje za kladné číslo.

### <a name="lengths-of-exponents-and-mantissas"></a>Délky exponentů a mantisy

|Typ|Délka exponentu|Délka mantisy|
|----------|---------------------|---------------------|
|float|8 bitů|23 bitů|
|double|11 bitů|52 bitů|

Vzhledem k tomu, že exponenty jsou uloženy v nepodepsané formě, exponent je posunut o polovinu možné hodnoty. Pro typ float je posun 127; pro typ Double je to 1023. Skutečnou hodnotu exponent můžete vypočítat odečtením hodnoty bias od hodnoty exponent.

Mantisa je uložena jako binární zlomek větší nebo rovna 1 a menší než 2. Pro typy float a Double je v mantise v rámci nejvýznamnější bitové pozice implicitní počáteční 1, takže mantisy jsou ve skutečnosti 24 a 53 bity, a to i v případě, že je nejvýznamnější bit nikdy neuložený v paměti.

Místo toho, aby se právě popsala metoda úložiště, může balíček s plovoucí desetinnou čárkou obsahovat binární čísla s plovoucí desetinnou čárkou jako Denormalizovaná čísla. "Denormalizovaná čísla" jsou nenulová čísla s plovoucí desetinnou čárkou s hodnotami rezervovaných exponentů, ve kterých je nejvýznamnější bit mantisy 0. Pomocí denormalizovaného formátu lze rozsah čísla s plovoucí desetinnou čárkou rozšířit na náklady na přesnost. Nelze určit, zda je číslo s plovoucí desetinnou čárkou vyjádřeno v normalizovaném nebo denormalizovaném formátu. balíček s plovoucí desetinnou čárkou určuje reprezentace. Balíček s plovoucí desetinnou čárkou nikdy nepoužívá denormalizovanou formu, pokud exponent nebude menší než minimum, které lze znázornit v normalizované podobě.

V následující tabulce jsou uvedeny minimální a maximální hodnoty, které lze uložit v proměnných každého typu s plovoucí desetinnou čárkou. Hodnoty uvedené v této tabulce se vztahují jenom na normalizovaná čísla s plovoucí desetinnou čárkou. Denormalizovaná čísla s plovoucí desetinnou čárkou mají menší minimální hodnotu. Všimněte si, že čísla uchovávaná v registrech 80*x*87 jsou vždy reprezentovaná v normalizovaném formátu 80-bit. čísla lze reprezentovat pouze v denormalizovaném formátu při uložení v 32 nebo 64 proměnných s plovoucí desetinnou čárkou (proměnné typu float a typ Long).

### <a name="range-of-floating-point-types"></a>Rozsah typů s plovoucí desetinnou čárkou

|Typ|Minimální hodnota|Maximální hodnota|
|----------|-------------------|-------------------|
|float|1,175494351 E-38|3,402823466 E + 38|
|double|2.2250738585072014 E-308|1.7976931348623158 E + 308|

Pokud je přesnost menší z obav než úložiště, zvažte použití typu float pro proměnné s plovoucí desetinnou čárkou. Naopak, pokud je přesnost nejdůležitějším kritériem, použijte typ Double.

Proměnné s plovoucí desetinnou čárkou lze zvýšit na typ větší významnosti (z typu float na typ Double). K povýšení dochází často, když provádíte aritmetické proměnné s plovoucí desetinnou čárkou. Tato aritmetická operace je vždy prováděna jako vysoká úroveň přesnosti jako proměnná s nejvyšší mírou přesnosti. Zvažte například následující deklarace typů:

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

V předchozím příkladu je proměnná `f_short` povýšena na typ Double a vynásobena hodnotou; `f_long` pak je výsledek zaokrouhlen na typ float před přiřazením `f_short`.

V následujícím příkladu (který používá deklarace z předchozího příkladu) se aritmetické operace provádí v pohyblivé (32-bit) přesnosti proměnných. výsledek je pak povýšen na typ Double:

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
