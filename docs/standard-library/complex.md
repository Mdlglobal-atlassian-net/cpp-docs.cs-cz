---
title: '&lt;komplexní&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e6a8364c6f0491344eef7faf381d701944f66d9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965666"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Definuje kontejner šablony třídy `complex` a jeho podpůrných šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <complex>
```

## <a name="remarks"></a>Poznámky

Komplexní čísla je seřazená dvojice reálná čísla. Čistě geometrické řečeno je komplexní roviny real, dvourozměrné roviny. Speciální kvality roviny komplexní, které odlišují jej od skutečné roviny jsou z důvodu jeho existence další algebraických struktury. Tato struktura algebraických má dvě základní operace:

- Přidání definován jako (*a*, *b*) + (*c*, *d*) = (*a* + *c* , *b* + *d*)

- Definován jako násobení (*a*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad* + *bc*)

Sada komplexní čísla s operacemi komplexní sčítání a násobení složité je pole ve standardní algebraických smyslu:

- Operace sčítání a násobení jsou komutativní a asociativních a násobení distribuuje přes přidání přesně tak, jak to funguje se službou skutečné sčítání a násobení na pole reálná čísla.

- Komplexní čísla (0, 0) je additive identitu a (1, 0) je násobení identity.

- Inverzní doplňkové pro reprezentující komplexní čísla (*a*, *b*) je (-*a*, -*b*) a inverzní multiplicative pro takové komplexní čísla s výjimkou (0, 0) je

   (*a*/ (*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*a*<sup>2</sup> + *b*<sup>2</sup>))

Podle reprezentující komplexní čísla *z* = (*a*, *b*) ve formátu *z* = *a*  +  *bi*, kde *i*<sup>2</sup> = -1, pravidla pro algebra sadu reálná čísla můžete použít sadu komplexní čísla a jejich součástí. Příklad:

   (1 + 2*můžu*) \* (2 + 3*můžu*)  
   = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*)  
   = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
   = (2 – 6) + (3 + 4)*mi*  
   = -4 + 7*i*

Systém komplexní čísla je pole, ale není seřazené pole. Neexistuje žádné řazení komplexních čísel, protože není pro pole reálná čísla a její podskupiny, takže nerovností nelze použít pro komplexní čísla, jako jsou na reálná čísla.

Existují tři běžné formuláře reprezentující komplexní čísla *z*:

- Kartézských: *z* = *a* + *bi*

- Polární: *z* = *r* (cos *p* + *můžu* sin *p*)

- Exponenciální: *z* = *r* \* *e*<sup>*ip*</sup>

Termíny používané v těchto standardní reprezentace komplexního čísla označují následujícím způsobem:

- Skutečně kartézských součásti nebo skutečné část *a*.

- Imaginární Kartézském nebo imaginární části *b*.

- Modulus nebo absolutní hodnotu čísla komplexní *r*.

- Úhel argument nebo fázi *p* v radiánech.

Pokud není uvedeno jinak, jsou funkce, které může vrátit více hodnot musí vrátit hodnotu instančního objektu pro své argumenty větší než - pí a menší než nebo rovno + pí Novoroční jeden s hodnotou. Musí být vyjádřena všechny jedná o úhly v radiánech, kde jsou v kruhu 2π radiány (360 ° f).

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Abs](../standard-library/complex-functions.md#abs)|Vypočítá zbytek z komplexního čísla.|
|[arg](../standard-library/complex-functions.md#arg)|Extrahuje argumentu z komplexního čísla.|
|[conj](../standard-library/complex-functions.md#conj)|Vrátí sdružené komplexního čísla.|
|[Cos](../standard-library/complex-functions.md#cos)|Vrátí hodnotu kosinus tohoto komplexního čísla.|
|[COSH –](../standard-library/complex-functions.md#cosh)|Vrací hyperbolický kosinus komplexního čísla.|
|[exp](../standard-library/complex-functions.md#exp)|Vrátí hodnotu exponenciální funkce komplexního čísla.|
|[imag](../standard-library/complex-functions.md#imag)|Extrahuje imaginární komplexního čísla.|
|[protokol](../standard-library/complex-functions.md#log)|Vrátí přirozený logaritmus komplexního čísla.|
|[log10](../standard-library/complex-functions.md#log10)|Vrátí logaritmus o základu 10 komplexního čísla.|
|[Norm –](../standard-library/complex-functions.md#norm)|Extrahuje norm komplexního čísla.|
|[polar](../standard-library/complex-functions.md#polar)|Komplexní čísla, která odpovídá zadané operace modulo a argument, vrátí v Kartézském formuláře.|
|[Pow](../standard-library/complex-functions.md#pow)|Vyhodnotí komplexního čísla získala při vyvolání základ, který je komplexního čísla na mocninu vyjádřenou druhým číslem komplexní.|
|[Real](../standard-library/complex-functions.md#real)|Extrahuje reálnou součástí komplexního čísla.|
|[Sin](../standard-library/complex-functions.md#sin)|Vrátí sinus úhlu komplexního čísla.|
|[SINH –](../standard-library/complex-functions.md#sinh)|Vrací hyperbolický sinus komplexního čísla.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Vrátí druhou odmocninu komplexního čísla.|
|[Tan](../standard-library/complex-functions.md#tan)|Vrátí tangens komplexního čísla.|
|[TANH –](../standard-library/complex-functions.md#tanh)|Vrací hyperbolický tangens komplexního čísla.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testy pro nerovnost mezi dvěma komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[Operator *](../standard-library/complex-operators.md#op_star)|Vynásobí dvě komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[Operator +](../standard-library/complex-operators.md#op_add)|Přidá dvě komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[Operator-](../standard-library/complex-operators.md#operator-)|Odečte dva komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[Operator /](../standard-library/complex-operators.md#op_div)|Vydělí dvě komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[Operator <\<](../standard-library/complex-operators.md#op_lt_lt)|Funkce šablony, který se vkládá komplexního čísla do výstupního datového proudu.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Ověřuje rovnost mezi dvěma komplexní čísla, jeden nebo oba z nich může patřit do dílčí typ pro reálné a imaginární části.|
|[operátor >>](../standard-library/complex-operators.md#op_gt_gt)|Funkce šablony, který extrahuje komplexní hodnoty ze vstupního datového proudu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[komplexní\<double >](../standard-library/complex-double.md)|Třída explicitně specializovaný šablony popisuje objekt, který ukládá seřazená dvojice objektů, oba typu **double**, kde první představuje skutečný část komplexního čísla a druhá představuje imaginární části.|
|[complex\<float>](../standard-library/complex-float.md)|Třída explicitně specializovaný šablony popisuje objekt, který ukládá seřazená dvojice objektů, oba typu **float**, kde první představuje skutečný část komplexního čísla a druhá představuje imaginární části.|
|[komplexní\<long double >](../standard-library/complex-long-double.md)|Třída explicitně specializovaný šablony popisuje objekt, který ukládá seřazená dvojice objektů, oba typu **long double**, kde první představuje skutečný část komplexního čísla a druhá představuje imaginární části.|
|[complex](../standard-library/complex-class.md)|Třída šablony popisuje objekt, který používá reprezentující komplexní čísla systému a provádět komplexní aritmetické operace.|

### <a name="literals"></a>Literály

\<Komplexní > záhlaví definuje následující [uživateli definované literály](../cpp/user-defined-literals-cpp.md) který vytvoření komplexního čísla s skutečné část je nula a imaginární části se hodnota vstupního parametru.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Vrátí: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Vrátí: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Vrátí: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
