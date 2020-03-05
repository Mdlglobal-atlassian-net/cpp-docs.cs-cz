---
title: TraceInfo – třída
description: Referenční C++ dokumentace třídy TraceInfo sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332941"
---
# <a name="traceinfo-class"></a>TraceInfo – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TraceInfo` slouží k přístupu k užitečným vlastnostem týkajícím se analyzovaného nebo přeprotokolovaného trasování.

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

Ododečte `StartTimestamp` od `StopTimestamp` a Získá počet tiků uplynulých během celého trasování. Pomocí `TickFrequency` převeďte výslednou hodnotu na časovou jednotku. Příklad převodu taktů na čas naleznete v tématu [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Pokud nechcete, aby se osové značky převedly sami, třída `TraceInfo` poskytuje členskou funkci, která vrací dobu trasování v nanosekundách. Tuto hodnotu můžete C++ převést na jiné časové jednotky pomocí standardní knihovny `chrono`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Doba trvání](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>Úkolu

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet logických procesorů v počítači, kde bylo trasování shromážděno.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota Tick zachycená v době, kdy bylo trasování spuštěno.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota Tick zachycená v době, kdy bylo trasování zastaveno.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů za sekundu, které se použijí při vyhodnocování doby trvání měřené v taktech.

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *dat*
Data obsahující informace o trasování.

::: moniker-end
