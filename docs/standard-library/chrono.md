---
title: '&lt;typu chrono&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
dev_langs:
- C++
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d701b290100f812f3c7845096960561cb101472
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847491"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Zahrnují standardní hlavičku \<typu chrono > Definovat třídy a funkce, které představují a zpracování dobách trvání a okamžiky čas.

Od verze Visual Studio 2015, provádění `steady_clock` došlo ke změně splnění C++ Standard pro steadiness a monotonicity. `steady_clock` Nyní je založena na QueryPerformanceCounter() a `high_resolution_clock` je nyní typedef pro `steady_clock`. V důsledku toho v jazyce Visual C++ `steady_clock::time_point` je nyní typedef pro `chrono::time_point<steady_clock>`; ale to není nezbytně případ jiné implementace.

## <a name="syntax"></a>Syntaxe

```cpp
#include <chrono>
```

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[duration – třída](../standard-library/duration-class.md)|Popisuje typ, který obsahuje časovém intervalu.|
|[time_point – třída](../standard-library/time-point-class.md)|Popisuje typ, který reprezentuje bod v čase.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[common_type – struktura](../standard-library/common-type-structure.md)|Popisuje specializací třídy šablony [common_type](../standard-library/common-type-class.md) pro instancí možnosti `duration` a `time_point`.|
|[duration_values – struktura](../standard-library/duration-values-structure.md)|Poskytuje konkrétní hodnoty `duration` parametr šablony `Rep`.|
|[steady_clock – struktura](../standard-library/steady-clock-struct.md)|Představuje `steady` hodiny.|
|[system_clock – struktura](../standard-library/system-clock-structure.md)|Představuje *typ hodin* založený na systému v reálném čase hodiny.|
|[treat_as_floating_point – struktura](../standard-library/treat-as-floating-point-structure.md)|Určuje, zda lze typu zacházet jako s plovoucí desetinnou čárkou typu.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[duration_cast –](../standard-library/chrono-functions.md#duration_cast)|Přetypování `duration` objekt zadaného typu.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Přetypování `time_point` objekt zadaného typu.|

### <a name="operators"></a>Operátory

|Název|Popis|
|----------|-----------------|
|[Operator –](../standard-library/chrono-operators.md#operator-)|Operátor odčítání nebo negace `duration` a `time_point` objekty.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operátor nerovnosti, která se používá s `duration` nebo `time_point` objekty.|
|[Operátor modulo](../standard-library/chrono-operators.md#op_modulo)|Operátor pro modulo operací na `duration` objekty.|
|[operátor *](../standard-library/chrono-operators.md#op_star)|Operátor násobení pro `duration` objekty.|
|[operátor nebo](../standard-library/chrono-operators.md#op_div)|Operátor dělení pro `duration` objekty.|
|[operátor +](../standard-library/chrono-operators.md#op_add)|Přidá `duration` a `time_point` objekty.|
|[Operátor&lt;](../standard-library/chrono-operators.md#op_lt)|Určuje, zda jeden `duration` nebo `time_point` objektu je menší než jiná `duration` nebo `time_point` objektu.|
|[Operátor&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Určuje, zda jeden `duration` nebo `time_point` objektu je menší než nebo rovna do jiného `duration` nebo `time_point` objektu.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Určuje, zda dva `duration` představovat časové intervaly, které mají stejnou délku, nebo zda dvě `time_point` objekty představují stejného bodu v čase.|
|[Operátor&gt;](../standard-library/chrono-operators.md#op_gt)|Určuje, zda jeden `duration` nebo `time_point` je větší než druhý objekt `duration` nebo `time_point` objektu.|
|[Operátor&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Určuje, zda jeden `duration` nebo `time_point` objekt je větší než nebo rovna hodnotě jiného `duration` nebo `time_point` objektu.|

### <a name="predefined-duration-types"></a>Doba trvání předdefinované typy

Další informace o typech poměr, které se používají v následující definice TypeDef najdete v tématu [ \<poměr >](../standard-library/ratio.md).

|Definice TypeDef|Popis|
|-------------|-----------------|
|`typedef duration<long long, nano> nanoseconds;`|Synonymum pro `duration` typu, který má v jedné nanosecond intervalu značky.|
|`typedef duration<long long, micro> microseconds;`|Synonymum pro `duration` typu, který má v jedné mikrosekund intervalu značky.|
|`typedef duration<long long, milli> milliseconds;`|Synonymum pro `duration` typu, který má období značek jeden milisekundu.|
|`typedef duration<long long> seconds;`|Synonymum pro `duration` typu, který má období značek jednu sekundu.|
|`typedef duration<int, ratio<60> > minutes;`|Synonymum pro `duration` typu, který má období značek jednu minutu.|
|`typedef duration<int, ratio<3600> > hours;`|Synonymum pro `duration` typ, který má značek dobu jedné hodiny.|

### <a name="literals"></a>Literály

**(C ++ 11)**  \<Typu chrono > záhlaví definuje následující [uživateli definované literály](../cpp/user-defined-literals-cpp.md) používané pro větší pohodlí, bezpečnost typů a jeho udržovatelnost kódu. Tyto literály jsou definovány v `literals::chrono_literals` vložené obor názvů a jsou v oboru, kdy std::chrono nachází v oboru.

|Literál|Popis|
|-------------|-----------------|
|operátor chrono::hours "" h (bez znaménka dlouho dlouhá hodnota)|Určuje čas jako celočíselné hodnoty.|
|chrono::Duration\<double, poměr\<3600 >> operátor "" h (long double Val)|Určuje čas jako hodnotu s plovoucí desetinnou čárkou.|
|chrono::minutes (operátor "" min) (bez znaménka dlouho dlouhá hodnota)|Určuje počet minut jako celočíselné hodnoty.|
|chrono::Duration\<double, poměr\<60 >> (operátor "" min) (dlouho dvakrát Val)|Určuje počet minut jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::seconds "" s (bez znaménka dlouho dlouhá hodnota)|Určuje počet minut jako celočíselné hodnoty.|
|chrono::Duration\<dvojité > operátor "" s (long double Val)|Určuje v sekundách jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::milliseconds "" ms (bez znaménka dlouho dlouhá hodnota)|Určuje počet milisekund jako celočíselné hodnoty.|
|chrono::Duration\<double, milli > operátor "" ms (long double Val)|Určuje počet milisekund jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::microseconds "" nám (bez znaménka dlouho dlouhá hodnota)|Určuje mikrosekundách jako celočíselné hodnoty.|
|chrono::Duration\<double, micro > operátor "" nám (long double Val)|Určuje mikrosekundách jako hodnotu s plovoucí desetinnou čárkou.|
|operátor chrono::nanoseconds "" ns (bez znaménka dlouho dlouhá hodnota)|Určuje nanosekundách jako celočíselné hodnoty.|
|chrono::Duration\<double, nano > operátor "" ns (long double Val)|Určuje nanosekundách jako hodnotu s plovoucí desetinnou čárkou.|
|||

Následující příklady ukazují, jak používat literály typu chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
