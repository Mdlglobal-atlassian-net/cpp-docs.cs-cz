---
title: '&lt;complex &gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 071e9369cdd0469d8ddc1c6649a3801732d8e23f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688222"
---
# <a name="ltcomplexgt"></a>&lt;complex &gt;

Definuje šablonu třídy kontejneru `complex` a její podpůrné šablony.

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<complex >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Komplexní číslo je řazená dvojice reálných čísel. V čistě geograficky geometrických výrazech je složitá rovina skutečnou dvourozměrnou rovinou. Speciálními kvalitami komplexní roviny, které ji odlišují od skutečné roviny, jsou vzhledem k tomu, že mají další strukturu algebraických. Tato struktura algebraických má dvě základní operace:

- Přidání definované jako (*a*, *b*) + (*c*, *d*) = ( * + * *c*, *b*  + *d*)

- Násobení definované jako (*a*, *b*) \* (*c*, *d*) = (*AC*  - *BD*, *AD*  + *BC*)

Sada komplexních čísel s operacemi komplexního sčítání a komplexního násobení je pole ve standardním algebraických smyslu:

- Operace sčítání a násobení jsou komutativní a asociativní a nenásobení, které se přidávají přesně stejně jako v případě skutečného sčítání a násobení v poli reálných čísel.

- Komplexní číslo (0, 0) je doplňková identita a (1, 0) je identita multiplikativní.

- Doplňková inverzní hodnota pro komplexní číslo (*a*, *b*) je (-*a*,-*b*) a multiplikativní INVERT pro všechna taková komplexní čísla s výjimkou (0, 0) je.

   (*a/* (*a*<sup>2</sup>  + *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  + *b*<sup>2</sup>))

Výsledkem představuje komplexní číslo *z* = (*a*, *b*) ve tvaru *z* * =   + * *BI*, kde *i*<sup>2</sup> =-1, pravidla pro algebraický sady reálných čísel lze použít pro množinu komplexních hodnot. čísla a jejich součásti. Příklad:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7*i*

Systém komplexních čísel je pole, ale není seřazené pole. Neexistuje žádné řazení komplexních čísel, protože jsou pro pole reálných čísel a jejich podmnožiny, takže nerovnosti nelze použít na složitá čísla, protože se jedná o reálné číslo.

Existují tři běžné formy představující komplexní číslo *z*:

- Kartézském: *z*  =  * + * *BI*

- Polární: *z*  = *r* (cos *p*  + *i* Sin *p*)

- Exponenciální: *z*  = *r* \* *e*<sup>*IP adresa*</sup>

Výrazy používané v těchto standardních reprezentace komplexního čísla jsou označovány následujícím způsobem:

- Skutečná součást kartézském nebo skutečná část *a*.

- Imaginární část kartézském nebo imaginární část *b*.

- Zbytek nebo absolutní hodnota komplexního čísla *r*.

- Argument nebo úhel fáze *p* v radiánech.

Pokud není uvedeno jinak, funkce, které mohou vracet více hodnot, jsou požadovány pro vrácení objektu zabezpečení pro své argumenty větší než-π a menší nebo rovno + π, aby se zajistila jednotná hodnota. Všechny úhly musí být vyjádřeny v radiánech, kde jsou 2π radiány (360 stupňů) v kruhu.

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[ABS](../standard-library/complex-functions.md#abs)|Vypočítá zbytky komplexního čísla.|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh –](../standard-library/complex-functions.md#acosh)||
|[ARG](../standard-library/complex-functions.md#arg)|Extrahuje argument ze komplexního čísla.|
|[ASIN](../standard-library/complex-functions.md#asin)||
|[asinh –](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh –](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|Vrátí komplexní sdružené číslo se složitým číslem.|
|[Cos](../standard-library/complex-functions.md#cos)|Vrátí kosinus komplexního čísla.|
|[cosh –](../standard-library/complex-functions.md#cosh)|Vrací hyperbolický kosinus komplexního čísla.|
|[oček](../standard-library/complex-functions.md#exp)|Vrátí exponenciální funkci komplexního čísla.|
|[imag](../standard-library/complex-functions.md#imag)|Extrahuje imaginární komponentu komplexního čísla.|
|[protokolu](../standard-library/complex-functions.md#log)|Vrátí přirozený logaritmus komplexního čísla.|
|[log10 –](../standard-library/complex-functions.md#log10)|Vrátí logaritmus se základem 10 složeného čísla.|
|[Norm](../standard-library/complex-functions.md#norm)|Extrahuje normu komplexního čísla.|
|[polární](../standard-library/complex-functions.md#polar)|Vrátí komplexní číslo, které odpovídá specifikovaným modulům a argumentům ve formě kartézském.|
|[log](../standard-library/complex-functions.md#pow)|Vyhodnotí komplexní číslo získané vyvoláním základní třídy, která je komplexním číslem mocninou jiného komplexního čísla.|
|[Souhrn](../standard-library/complex-functions.md#proj)||
|[nemovitostí](../standard-library/complex-functions.md#real)|Extrahuje skutečnou komponentu komplexního čísla.|
|[tlačítek](../standard-library/complex-functions.md#sin)|Vrátí sinus komplexního čísla.|
|[sinh –](../standard-library/complex-functions.md#sinh)|Vrátí hyperbolický sinus komplexního čísla.|
|[SQRT](../standard-library/complex-functions.md#sqrt)|Vrátí druhou odmocninu složeného čísla.|
|[nádrž](../standard-library/complex-functions.md#tan)|Vrací tangens komplexního čísla.|
|[tanh –](../standard-library/complex-functions.md#tanh)|Vrací hyperbolický tangens komplexního čísla.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testy nerovnosti mezi dvěma komplexními čísly, jednu nebo obě mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[podnikatel](../standard-library/complex-operators.md#op_star)|Vynásobí dvě složitá čísla, jedno nebo obě, které mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[operator + – operátor](../standard-library/complex-operators.md#op_add)|Přidává dvě složitá čísla, jedno nebo obě, které mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[podnikatel](../standard-library/complex-operators.md#operator-)|Odečte dvě složitá čísla, jedno nebo obě, které mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[podnikatel](../standard-library/complex-operators.md#op_div)|Rozdělí dvě složitá čísla, jedno nebo obě, které mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[operátor < \<](../standard-library/complex-operators.md#op_lt_lt)|Funkce šablony, která vloží komplexní číslo do výstupního datového proudu.|
|[operator = = – operátor](../standard-library/complex-operators.md#op_eq_eq)|Testy pro rovnost mezi dvěma komplexními čísly, jeden nebo oba, které mohou patřit do podmnožiny typu pro reálné a imaginární části.|
|[operátor > >](../standard-library/complex-operators.md#op_gt_gt)|Funkce šablony, která extrahuje komplexní hodnotu ze vstupního datového proudu.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[komplexní \<double >](../standard-library/complex-double.md)|Explicitně specializovaná šablona třídy popisuje objekt, který ukládá seřazený pár objektů ( **Double typu Double**, kde první představuje skutečnou část komplexního čísla a druhý představuje imaginární část).|
|[komplexní \<float >](../standard-library/complex-float.md)|Explicitně specializovaná šablona třídy popisuje objekt, který ukládá seřazený pár objektů, oba typy **float**, kde první představuje reálnou část komplexního čísla a druhá představuje imaginární část.|
|[> \<long Double](../standard-library/complex-long-double.md)|Explicitně specializovaná šablona třídy popisuje objekt, který ukládá seřazený pár objektů, jak typu **Long Double**, kde první představuje reálnou část komplexního čísla a druhý představuje imaginární část.|
|[složit](../standard-library/complex-class.md)|Šablona třídy popisuje objekt použitý k reprezentaci komplexního číselného systému a provádění složitých aritmetických operací.|

### <a name="literals"></a>Literály

Hlavička \<complex > definuje následující [uživatelsky definované literály](../cpp/user-defined-literals-cpp.md) , které vytvoří komplexní číslo s reálnou částí nula a imaginární část je hodnota vstupního parametru.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Vrátí: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Vrátí: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Vrátí: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
