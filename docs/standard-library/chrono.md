---
title: '&lt;chrono&gt;'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: 904e4df6b6c16b846ab4417d24a1d9836380d75b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544544"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Zahrnout standardní hlavička \<chrono > k definování třídy a funkce, které představují a manipulaci s dob trvání a okamžiky čas.

V sadě Visual Studio 2015, provádění od `steady_clock` došlo ke změně pro splnění požadavků standardu C++ steadiness a monotonicity. `steady_clock` Teď vychází QueryPerformanceCounter() a `high_resolution_clock` je nyní definice typu `steady_clock`. V důsledku toho v jazyce Visual C++ `steady_clock::time_point` je nyní definice typu `chrono::time_point<steady_clock>`, nicméně toto není nutně případ v jiných implementacích.

## <a name="syntax"></a>Syntaxe

```cpp
#include <chrono>
```

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[duration – třída](../standard-library/duration-class.md)|Popisuje typ, který obsahuje časový interval.|
|[time_point – třída](../standard-library/time-point-class.md)|Popisuje typ, který představuje bod v čase.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[common_type – struktura](../standard-library/common-type-structure.md)|Popisuje specializace třídy šablony [common_type](../standard-library/common-type-class.md) pro konkretizací `duration` a `time_point`.|
|[duration_values – struktura](../standard-library/duration-values-structure.md)|Poskytuje specifické hodnoty pro `duration` parametr šablony `Rep`.|
|[steady_clock – struktura](../standard-library/steady-clock-struct.md)|Představuje `steady` hodiny.|
|[system_clock – struktura](../standard-library/system-clock-structure.md)|Představuje *typ hodin* , který je založen na reálného času systému.|
|[treat_as_floating_point – struktura](../standard-library/treat-as-floating-point-structure.md)|Určuje, zda typ lze považovat za typ s plovoucí desetinnou čárkou.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[duration_cast –](../standard-library/chrono-functions.md#duration_cast)|Přetypování `duration` objekt zadaného typu.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Přetypování `time_point` objekt zadaného typu.|

### <a name="operators"></a>Operátory

|Název|Popis|
|----------|-----------------|
|[Operator-](../standard-library/chrono-operators.md#operator-)|Operátor odčítání nebo negace objektů `duration` a `time_point` objekty.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operátor nerovnosti, který se používá s `duration` nebo `time_point` objekty.|
|[Operátor modulo](../standard-library/chrono-operators.md#op_modulo)|Operátor modulo operace `duration` objekty.|
|[Operator *](../standard-library/chrono-operators.md#op_star)|Operátor násobení pro `duration` objekty.|
|[Operator /](../standard-library/chrono-operators.md#op_div)|Operátor dělení pro `duration` objekty.|
|[Operator +](../standard-library/chrono-operators.md#op_add)|Přidá `duration` a `time_point` objekty.|
|[– Operátor&lt;](../standard-library/chrono-operators.md#op_lt)|Určuje, zda jeden `duration` nebo `time_point` je menší než jiný objekt `duration` nebo `time_point` objektu.|
|[– Operátor&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Určuje, zda jeden `duration` nebo `time_point` objekt je menší nebo rovna jiné `duration` nebo `time_point` objektu.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Určuje, zda dva `duration` objekty představují časové intervaly, které mají stejnou délku, nebo zda dva `time_point` objekty představují stejný bod v čase.|
|[– Operátor&gt;](../standard-library/chrono-operators.md#op_gt)|Určuje, zda jeden `duration` nebo `time_point` je větší než jiný objekt `duration` nebo `time_point` objektu.|
|[– Operátor&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Určuje, zda jeden `duration` nebo `time_point` objekt je větší než nebo roven jinému `duration` nebo `time_point` objektu.|

### <a name="predefined-duration-types"></a>Doba trvání předdefinované typy

Další informace o poměr typy, které se používají v následujících – definice TypeDef, naleznete v tématu [ \<poměr >](../standard-library/ratio.md).

|Definice TypeDef|Popis|
|-------------|-----------------|
|`typedef duration<long long, nano> nanoseconds;`|Synonymum pro `duration` typ, který má jeden nanosekund s dobou značek.|
|`typedef duration<long long, micro> microseconds;`|Synonymum pro `duration` typ, který má určitou značek jedné úrovni mikrosekund.|
|`typedef duration<long long, milli> milliseconds;`|Synonymum pro `duration` typ, který má jeden milisekund s dobou značek.|
|`typedef duration<long long> seconds;`|Synonymum pro `duration` typ, který má značek uplynutí jedné sekundy.|
|`typedef duration<int, ratio<60> > minutes;`|Synonymum pro `duration` typ, který má značek dobu jedné minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonymum pro `duration` typ, který má určitou značek jednu hodinu.|

### <a name="literals"></a>Literály

**(C ++ 11)**  \<Chrono > záhlaví definuje následující [uživateli definované literály](../cpp/user-defined-literals-cpp.md) , můžete použít pro větší pohodlí, bezpečnost typů a udržovatelnosti kódu. Tyto literály jsou definovány v `literals::chrono_literals` vložené obor názvů a jsou v oboru při std::chrono je v oboru.

|literál|Popis|
|-------------|-----------------|
|operátor chrono::hours "" h (unsigned long long Val)|Určuje hodiny jako celé číslo.|
|chrono::Duration\<double, poměr\<3600 >> operátor "" h (long double Val)|Určuje hodiny jako hodnotu s plovoucí desetinnou čárkou.|
|chrono::minutes (operátor "" min) (unsigned long long Val)|Určuje minuty jako celé číslo.|
|chrono::Duration\<double, poměr\<60 >> (operátor "" min) (long dvakrát Val)|Určuje minuty jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::seconds "" s (unsigned long long Val)|Určuje minuty jako celé číslo.|
|chrono::Duration\<double > – operátor "" s (long double Val)|Určuje sekundy jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::milliseconds "" ms (unsigned long long Val)|Určuje milisekundy jako celé číslo.|
|chrono::Duration\<double milli > – operátor "" ms (long double Val)|Určuje milisekundy jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::microseconds "" USA (unsigned long long Val)|Určuje mikrosekundy jako celé číslo.|
|chrono::Duration\<double micro > – operátor "" USA (long double Val)|Určuje mikrosekundy jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::nanoseconds "" ns (unsigned long long Val)|Určuje nanosekundách jako celé číslo.|
|chrono::Duration\<double nano > – operátor "" ns (long double Val)|Určuje nanosekundách jako hodnotu s plovoucí desetinnou čárkou.|
|||

Následující příklady ukazují, jak používat literály typu chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
