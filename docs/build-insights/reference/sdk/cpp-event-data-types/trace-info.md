---
title: TraceInfo třída
description: C++ Build Insights SDK TraceInfo odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324177"
---
# <a name="traceinfo-class"></a>TraceInfo třída

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TraceInfo` se používá pro přístup k užitečné vlastnosti o trasování analyzovány nebo relogged.

## <a name="syntax"></a>Syntaxe

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>Poznámky

Odečíst `StartTimestamp` od `StopTimestamp` získat počet klíšťat uplynulběhem celé trasování. Slouží `TickFrequency` k převodu výsledné hodnoty na časovou jednotku. Příklad převodu značek na čas naleznete [v tématu EVENT_DATA](../c-event-data-types/event-data-struct.md).

Pokud nechcete převést značky sami, `TraceInfo` třída poskytuje členská funkce, která vrací dobu trvání trasování v nanosekundách. Pomocí standardní knihovny `chrono` Jazyka C++ převeďte tuto hodnotu na jiné časové jednotky.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Doba trvání](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>Doba trvání

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>Logický počet procesorů

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet logických procesorů v počítači, kde byla trasování shromážděna.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimerazítko

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota značky zachycená v době spuštění trasování.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimerazítko

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota značky zachycená v době, kdy bylo trasování zastaveno.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Frekvence zaškrtnutí

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet klíšťat za sekundu, které se mají použít při hodnocení doby trvání měřené v klíšťacích.

## <a name="traceinfo"></a><a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parametry

*Dat*\
Data obsahující informace o trasování.

::: moniker-end
