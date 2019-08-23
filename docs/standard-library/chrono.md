---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: b3352110c2074b325ac345c05dbf899c0bdbd0ab
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975911"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Zahrňte standardní hlavičku \<Chrono > k definování tříd a funkcí, které reprezentují časová období a časová období.

Počínaje verzí `steady_clock` Visual Studio 2015 se implementace nástroje změnila tak, aby splňovala C++ standardní požadavky na Steadiness a monotonicity. `steady_clock`je nyní založen na QueryPerformanceCounter () a `high_resolution_clock` je nyní definicí pro `steady_clock`. V důsledku toho je teď v kompilátoru C++ `steady_clock::time_point` od Microsoftu definice typu pro `chrono::time_point<steady_clock>`; toto pravidlo ale nutně neplatí pro jiné implementace.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[duration – třída](../standard-library/duration-class.md)|Popisuje typ, který obsahuje časový interval.|
|[time_point – třída](../standard-library/time-point-class.md)|Popisuje typ, který představuje bod v čase.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[common_type – struktura](../standard-library/common-type-structure.md)|Popisuje specializace třídy template [common_type](../standard-library/common-type-class.md) pro instance `duration` a. `time_point`|
|[duration_values – struktura](../standard-library/duration-values-structure.md)|Poskytuje konkrétní hodnoty pro `duration` parametr `Rep`šablony.|
|[high_resolution_clock – struktura](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock – struktura](../standard-library/steady-clock-struct.md)|`steady` Představuje hodiny.|
|[system_clock – struktura](../standard-library/system-clock-structure.md)|Představuje *typ hodin* , který je založen na hodinách systému v reálném čase.|
|[treat_as_floating_point – struktura](../standard-library/treat-as-floating-point-structure.md)|Určuje, zda typ lze považovat za typ s plovoucí desetinnou čárkou.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Přetypování `duration` objektu na zadaný typ.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Přetypování `time_point` objektu na zadaný typ.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel](../standard-library/chrono-operators.md#operator-)|Operátor pro odčítání nebo negaci `duration` objektů a. `time_point`|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operátor nerovnosti, který se používá `duration` s `time_point` objekty nebo.|
|[Operátor modulo](../standard-library/chrono-operators.md#op_modulo)|Operátor pro operace modulo s `duration` objekty.|
|[podnikatel](../standard-library/chrono-operators.md#op_star)|Operátor násobení pro `duration` objekty|
|[podnikatel](../standard-library/chrono-operators.md#op_div)|Operátor dělení pro `duration` objekty.|
|[operator + – operátor](../standard-library/chrono-operators.md#op_add)|Přidá `duration` objekty `time_point` a.|
|[podnikatel&lt;](../standard-library/chrono-operators.md#op_lt)|Určuje, zda `duration` je `time_point` jeden objekt nebo objekt menší `duration` než `time_point` jiný objekt nebo.|
|[podnikatel&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Určuje, zda `duration` je `time_point` jeden objekt nebo objekt menší nebo roven jinému `duration` objektu `time_point` nebo.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Určuje, zda `duration` dva objekty reprezentují časové intervaly, které mají stejnou délku `time_point` , nebo zda dva objekty reprezentují stejný bod v čase.|
|[podnikatel&gt;](../standard-library/chrono-operators.md#op_gt)|Určuje, zda `duration` je `time_point` jeden objekt nebo objekt větší `duration` než `time_point` jiný objekt nebo.|
|[podnikatel&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Určuje, zda `duration` je `time_point` jeden objekt nebo objekt větší nebo roven jinému `duration` objektu `time_point` nebo.|

### <a name="typedefs-predefined-duration-types"></a>Definice typedef (předdefinované typy doby trvání)

Další informace o typech poměrů, které jsou používány v následujících definice typedef, naleznete v tématu [ \<poměr >](../standard-library/ratio.md).

|||
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Synonymum pro `duration` typ, který má období zatržení 1 nanosekund.|
|`typedef duration<long long, micro> microseconds;`|Synonymum pro `duration` typ, který má období zatržení 1 mikrosekunda.|
|`typedef duration<long long, milli> milliseconds;`|Synonymum pro `duration` typ, který má období zatržení 1 milisekundu.|
|`typedef duration<long long> seconds;`|Synonymum pro `duration` typ, který má období Tick 1 sekunda.|
|`typedef duration<int, ratio<60> > minutes;`|Synonymum pro `duration` typ, který má období zatržení 1 minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonymum pro `duration` typ, který má období zatržení 1 hodina.|

### <a name="literals"></a>Literály

**(C++ 11)** Hlavička > Chrono definuje následující uživatelsky [definované literály](../cpp/user-defined-literals-cpp.md) , které lze použít pro lepší pohodlí, typově bezpečnost a udržovatelnost kódu. \< Tyto literály jsou definovány v `literals::chrono_literals` oboru názvů inline a jsou v oboru, pokud je v oboru definováno std:: chrono.

|||
|-|-|
|hodiny – operátor "" h (unsigned long long Val)|Určuje hodiny jako celočíselnou hodnotu.|
|Dvojitá doba\<trvání\<, poměr 3 600 > > operátor "" h (long double Val)|Určuje hodiny jako hodnotu s plovoucí desetinnou čárkou.|
|minut (operátor "" min) (nepodepsaný dlouhý dlouhý formát)|Určuje minuty jako integrální hodnoty.|
|Dvojitá doba\<trvání\<, poměr 60 > > (operátor "" min.) (long double Val)|Určuje minuty jako hodnotu s plovoucí desetinnou čárkou.|
|sekundový operátor "" s (unsigned long long Val)|Určuje minuty jako integrální hodnoty.|
|Dvojitá délka\<> operátoru "" s (long double Val)|Určuje sekundy jako hodnotu s plovoucí desetinnou čárkou.|
|MS (milisekundy) – operátor MS (unsigned long long Val)|Určuje milisekundy jako celočíselnou hodnotu.|
|Dvojitá doba trvání\<, lisovny > operátor "" MS (long double Val)|Určuje milisekundy jako hodnotu s plovoucí desetinnou čárkou.|
|mikrosekundový operátor "" US (nepodepsaná Long Long Val)|Určuje mikrosekundy jako celočíselnou hodnotu.|
|Dvojitá doba trvání\<, mikro > operátor USA (long double Val)|Určuje mikrosekundy jako hodnotu s plovoucí desetinnou čárkou.|
|"– operátor nanosekund" "NS (unsigned long long long Val)|Určuje nanosekundy jako celočíselnou hodnotu.|
|Dvojitá doba trvání\<, operátor nano > "" NS (long double Val)|Určuje nanosekundy jako hodnotu s plovoucí desetinnou čárkou.|

Následující příklady ukazují, jak používat literály Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
