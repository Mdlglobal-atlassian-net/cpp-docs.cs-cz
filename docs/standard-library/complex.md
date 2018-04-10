---
title: '&lt;komplexní&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e23707a342e666e49a15c47e0dc82c4e882176cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;
Definuje třídu šablony kontejneru **komplexní** a jeho podpůrné šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <complex>  
```  
  
## <a name="remarks"></a>Poznámky  
 Komplexní čísla je dvojici seřazený v reálná čísla. V čistě geometrické podmínky je komplexní roviny skutečné, dvourozměrné roviny. Zvláštní roviny komplexní vlastnosti, které ho odlišuje od skutečné roviny jsou z důvodu jeho s další algebraických strukturu. Tato struktura algebraických má dvě základní operace:  
  
-   Přidání definován jako (*a*, *b*) + (*c*, *d*) = (*a* + *c* , *b* + *d*)  
  
-   Definován jako násobení (*a*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad* + *bc*)  
  
 Sada komplexní čísla s operacemi složité přidání a komplexní násobení jsou pole v tom smyslu, standardní algebraických:  
  
-   Operace přidání a násobení jsou komutativní a asociativní a násobení distribuuje přes přidání přesně tak, jak tomu u skutečné sčítání a násobení na poli reálných čísel.  
  
-   Komplexní čísla (0, 0) je doplňkové identity a (1, 0) se multiplikativní identitu.  
  
-   Inverzní doplňkové pro reprezentující komplexní čísla (*a*, *b*) je (-*a*, -*b*) a inverzní multiplicative pro takové komplexní čísla s výjimkou (0, 0) je  
  
     (*a*/ (*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*a*<sup>2</sup> + *b*<sup>2</sup>))  
  
 Podle reprezentující komplexní čísla *z* = (*a*, *b*) ve formátu *z* = *a*  +  *bi*, kde *i*<sup>2</sup> = -1, pravidla pro algebra sadu reálná čísla můžete použít sadu komplexní čísla a jejich součástí. Příklad:  
  
  (1 + 2*i*) \* (2 + 3*i*)  
  = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*)  
  = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
  = (2 - 6) + (3 + 4)*i*  
  = -4 + 7*i*  
  
 Tento systém komplexní čísla je pole, ale není uspořádaného pole. Není žádný řazení komplexní čísla, jak se pole reálná čísla a jeho podmnožiny, takže nerovnosti nelze použít pro komplexní čísla, protože se jedná o pro reálná čísla.  
  
 Existují tři běžné formy reprezentující komplexní čísla *z*:  
  
-   Kartézských: *z* = *a* + *bi*  
  
-   Polárního: *z* = *r* (cos *p* + *i* sin *p*)  
  
-   Exponenciální: *z* = *r* \* *e*<sup>*ip*</sup>  
  
 Termínů používaných v těchto standardní reprezentace komplexního čísla se označují takto:  
  
-   Skutečně kartézských součásti nebo skutečné část *a*.  
  
-   Pomyslná kartézských součásti nebo pomyslná část *b*.  
  
-   Modulus nebo absolutní hodnota čísla komplexní *r*.  
  
-   Úhel argument, nebo fáze *p* v radiánech.  
  
 Pokud není uvedeno jinak, jsou funkce, které může vrátit více hodnot musí vrátit hodnotu hlavní pro jejich argumenty větší než - pí a menší než nebo rovno + pí, abyste zajistili jejich jeden s hodnotou. Všechny úhly musí být vyjádřena v radiánech, kde je 2π radiánech (360 stupňů) v kruh.  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[Abs](../standard-library/complex-functions.md#abs)|Vypočítá numerického zbytku komplexního čísla.|  
|[arg](../standard-library/complex-functions.md#arg)|Extrahuje argument z komplexního čísla.|  
|[conj](../standard-library/complex-functions.md#conj)|Vrátí sdružené komplexního čísla.|  
|[Cos](../standard-library/complex-functions.md#cos)|Vrací kosinus komplexního čísla.|  
|[cosh](../standard-library/complex-functions.md#cosh)|Vrátí hyperbolický kosinus čísla komplexní.|  
|[exp](../standard-library/complex-functions.md#exp)|Vrátí hodnotu exponenciálního komplexního čísla.|  
|[imag](../standard-library/complex-functions.md#imag)|Extrahuje komponentu pomyslná komplexního čísla.|  
|[log](../standard-library/complex-functions.md#log)|Vrátí přirozený logaritmus čísla komplexní.|  
|[log10](../standard-library/complex-functions.md#log10)|Vrátí logaritmus o základu 10 komplexního čísla.|  
|[Norm](../standard-library/complex-functions.md#norm)|Extrahuje norm komplexního čísla.|  
|[polar](../standard-library/complex-functions.md#polar)|Vrátí číslo komplexní, který odpovídá zadané numerického zbytku a argument, kartézských formuláře.|  
|[pow](../standard-library/complex-functions.md#pow)|Vyhodnotí komplexního čísla získala při vyvolání základ, který je komplexní číslo na mocninu vyjádřenou druhým číslem komplexní.|  
|[real](../standard-library/complex-functions.md#real)|Extrahuje komponentu skutečné komplexního čísla.|  
|[sin](../standard-library/complex-functions.md#sin)|Vrátí sinus komplexního čísla.|  
|[sinh](../standard-library/complex-functions.md#sinh)|Vrátí hyperbolický sinus čísla komplexní.|  
|[sqrt](../standard-library/complex-functions.md#sqrt)|Vrátí druhou odmocninu komplexního čísla.|  
|[tan](../standard-library/complex-functions.md#tan)|Vrátí tangens čísla komplexní.|  
|[tanh](../standard-library/complex-functions.md#tanh)|Vrátí hyperbolický tangens čísla komplexní.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testy nerovnost mezi dvěma komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.|  
|[operátor *](../standard-library/complex-operators.md#op_star)|Vynásobí dvě komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.|  
|[operator+](../standard-library/complex-operators.md#op_add)|Přidá dvě komplexní čísla, jednu nebo obě dvě může patřit k podmnožině typ pro skutečné a pomyslná části.|  
|[operator-](../standard-library/complex-operators.md#operator-)|Odečítá od dva komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.|  
|[operátor nebo](../standard-library/complex-operators.md#op_div)|Vydělí dvě komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.|  
|[operátor <\<](../standard-library/complex-operators.md#op_lt_lt)|Funkce šablony, která vloží komplexního čísla do výstupního datového proudu.|  
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Testování rovnosti mezi dvěma komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.|  
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Funkce šablony, která extrahuje komplexní hodnoty ze vstupního datového proudu.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[komplexní\<dvojité >](../standard-library/complex-double.md)|Třída explicitně specializované šablony popisuje objekt, který ukládá dvojici seřazené objektů, obě typu **dvojité**, kde první reprezentuje část skutečné komplexního čísla a druhý reprezentuje část pomyslná.|  
|[complex\<float>](../standard-library/complex-float.md)|Třída explicitně specializované šablony popisuje objekt, který ukládá dvojici seřazené objektů, obě typu **float**, kde první reprezentuje část skutečné komplexního čísla a druhý reprezentuje část pomyslná.|  
|[komplexní\<long double >](../standard-library/complex-long-double.md)|Třída explicitně specializované šablony popisuje objekt, který ukládá dvojici seřazené objektů, obě typu **long double**, kde první reprezentuje část skutečné komplexního čísla a druhý reprezentuje část pomyslná.|  
|[complex](../standard-library/complex-class.md)|Šablony třídy popisuje objekt sloužící k představují komplexního čísla systému a provádět komplexní aritmetické operace.|  
  
### <a name="literals"></a>Literály  
 \<Komplexní > záhlaví definuje následující [uživateli definované literály](../cpp/user-defined-literals-cpp.md) který vytvořit komplexní číslo s skutečné část se nula a pomyslná část se hodnota vstupní parametr.  
  
|||  
|-|-|  
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Vrátí: `complex<long double>{0.0L, static_cast<long double>(d)}`|  
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Vrátí: `complex<double>{0.0, static_cast<double>(d)}`.|  
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Vrátí: `complex<float>{0.0f, static_cast<float>(d)}`.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



