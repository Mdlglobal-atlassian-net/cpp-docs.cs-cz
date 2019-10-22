---
title: '&lt;chrono &gt;'
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
ms.openlocfilehash: e27ff146c75da6e90e6336106beba714dbe7c8a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689869"
---
# <a name="ltchronogt"></a>&lt;chrono &gt;

Zahrňte standardní hlavičku \<chrono > k definování tříd a funkcí, které reprezentují časová období a časová období.

Počínaje verzí Visual Studio 2015 se implementace `steady_clock` změnila tak, aby splňovala C++ standardní požadavky na Steadiness a monotonicity. `steady_clock` je nyní založen na QueryPerformanceCounter () a `high_resolution_clock` je nyní definicí pro `steady_clock`. V důsledku toho je v kompilátoru Microsoft C++ `steady_clock::time_point` nyní definice pro `chrono::time_point<steady_clock>`; Toto pravidlo ale nutně neplatí pro jiné implementace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

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
|[common_type – struktura](../standard-library/common-type-structure.md)|Popisuje specializace šablony třídy [common_type](../standard-library/common-type-class.md) pro vytváření instancí `duration` a `time_point`.|
|[duration_values – struktura](../standard-library/duration-values-structure.md)|Poskytuje konkrétní hodnoty pro `duration` parametr šablony `Rep`.|
|[high_resolution_clock – struktura](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock – struktura](../standard-library/steady-clock-struct.md)|Představuje `steady` hodiny.|
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
|[podnikatel](../standard-library/chrono-operators.md#operator-)|Operátor pro odčítání nebo negaci objektů `duration` a `time_point`|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operátor nerovnosti, který se používá s objekty `duration` nebo `time_point`.|
|[Operátor modulo](../standard-library/chrono-operators.md#op_modulo)|Operátor pro operace modulo u objektů `duration`.|
|[podnikatel](../standard-library/chrono-operators.md#op_star)|Operátor násobení pro objekty `duration`.|
|[podnikatel](../standard-library/chrono-operators.md#op_div)|Operátor dělení pro objekty `duration`.|
|[operator + – operátor](../standard-library/chrono-operators.md#op_add)|Přidá objekty `duration` a `time_point`.|
|[operátor &lt;](../standard-library/chrono-operators.md#op_lt)|Určuje, zda jeden `duration` nebo `time_point` objekt je menší než jiný objekt `duration` nebo `time_point`.|
|[operátor &lt; =](../standard-library/chrono-operators.md#op_lt_eq)|Určuje, zda jeden `duration` nebo `time_point` objekt je menší nebo roven jinému `duration` nebo objektu `time_point`.|
|[operator = = – operátor](../standard-library/chrono-operators.md#op_eq_eq)|Určuje, zda dva objekty `duration` reprezentují časové intervaly, které mají stejnou délku, nebo zda dva objekty `time_point` reprezentují stejný bod v čase.|
|[operátor &gt;](../standard-library/chrono-operators.md#op_gt)|Určuje, zda jeden `duration` nebo `time_point` objekt je větší než jiný objekt `duration` nebo objekt `time_point`.|
|[operátor &gt; =](../standard-library/chrono-operators.md#op_gt_eq)|Určuje, zda jeden `duration` nebo `time_point` objekt je větší nebo roven jinému `duration` nebo objektu `time_point`.|

### <a name="typedefs-predefined-duration-types"></a>Definice typedef (předdefinované typy doby trvání)

Další informace o typech poměrů, které jsou používány v následujících definice typedef, naleznete v tématu [\<ratio >](../standard-library/ratio.md).

|||
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Synonymum pro typ `duration`, který má období zatržení 1 nanosekund.|
|`typedef duration<long long, micro> microseconds;`|Synonymum pro typ `duration`, který má tečku na začátku 1 sekundu.|
|`typedef duration<long long, milli> milliseconds;`|Synonymum pro typ `duration`, který má období zatržení 1 milisekundu.|
|`typedef duration<long long> seconds;`|Synonymum pro typ `duration`, který má období zatržení 1 sekundu.|
|`typedef duration<int, ratio<60> > minutes;`|Synonymum pro typ `duration`, který má období zatržení 1 minuta.|
|`typedef duration<int, ratio<3600> > hours;`|Synonymum pro typ `duration`, který má období zatržení 1 hodina.|

### <a name="literals"></a>Literály

**(C++ 11)** Hlavička \<chrono > definuje následující [uživatelsky definované literály](../cpp/user-defined-literals-cpp.md) , které lze použít pro lepší pohodlí, bezpečnost typů a udržovatelnost kódu. Tyto literály jsou definovány v `literals::chrono_literals` vloženém oboru názvů a jsou v oboru, pokud je v oboru std:: chrono.

|||
|-|-|
|hodiny – operátor "" h (unsigned long long Val)|Určuje hodiny jako celočíselnou hodnotu.|
|Trvání \<double, poměr \<3600 > > operátor "" h (long double Val)|Určuje hodiny jako hodnotu s plovoucí desetinnou čárkou.|
|minut (operátor "" min) (nepodepsaný dlouhý dlouhý formát)|Určuje minuty jako integrální hodnoty.|
|Trvání \<double, poměr \<60 > > (operátor "" min. ") (long double Val)|Určuje minuty jako hodnotu s plovoucí desetinnou čárkou.|
|sekundový operátor "" s (unsigned long long Val)|Určuje minuty jako integrální hodnoty.|
|Trvání \<double > operátorem "" s (long double Val)|Určuje sekundy jako hodnotu s plovoucí desetinnou čárkou.|
|MS (milisekundy) – operátor MS (unsigned long long Val)|Určuje milisekundy jako celočíselnou hodnotu.|
|Trvání \<double, Mill > operator "" MS (long double Val)|Určuje milisekundy jako hodnotu s plovoucí desetinnou čárkou.|
|mikrosekundový operátor "" US (nepodepsaná Long Long Val)|Určuje mikrosekundy jako celočíselnou hodnotu.|
|Trvání \<double, operátor Micro > (US) (long double Val)|Určuje mikrosekundy jako hodnotu s plovoucí desetinnou čárkou.|
|"– operátor nanosekund" "NS (unsigned long long long Val)|Určuje nanosekundy jako celočíselnou hodnotu.|
|Doba trvání \<double, operátor nano > "" NS (long double Val)|Určuje nanosekundy jako hodnotu s plovoucí desetinnou čárkou.|

Následující příklady ukazují, jak používat literály Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
