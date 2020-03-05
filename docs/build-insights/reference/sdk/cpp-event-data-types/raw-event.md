---
title: RawEvent – třída
description: Referenční C++ dokumentace třídy RawEvent sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333060"
---
# <a name="rawevent-class"></a>RawEvent – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `RawEvent` slouží k reprezentaci Obecné události v objektu [EventStack](event-stack.md).

## <a name="syntax"></a>Syntaxe

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Poznámky

Několik členských funkcí ve třídě `RawEvent` vrací počet impulsů. C++Build Insights používá čítač výkonu Windows jako zdroj taktů. Aby se počet impulsů převedl na časovou jednotku (sekundy), musí se použít interval impulsů. Je možné volat členskou funkci `TickFrequency` pro získání frekvence zaškrtnutí. Příklad, jak převést osové jednotky na časovou jednotku, najdete na stránce [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) .

Pokud nechcete, aby se osové značky převedly, třída `RawEvent` poskytuje členské funkce, které vracejí hodnoty času v nanosekundách. Pomocí standardní C++ knihovny `chrono` můžete převést nanosekundy na jiné časové jednotky.

## <a name="members"></a>Členové

### <a name="constructor"></a>Konstruktor

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
\ [dat](#data)
\ [doby trvání](#duration)
[Id události](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Id_procesu](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[Idvlákna](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parametry

\ *události*
Data události

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů procesoru, k nimž došlo během této aktivity. Takt procesoru se liší od normálního zaškrtnutí. Takty procesoru se počítají jenom v případě, že CPU spouští kód v aktivitě. Cykly procesoru se nepočítají, pokud je vlákno přidružené k aktivitě v režimu spánku.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba, po kterou CPU provádělo kód v rámci této aktivity. Tato hodnota může být vyšší než doba trvání aktivity, pokud jsou podřízené aktivity spouštěny v samostatných vláknech. Hodnota se vrátí v nanosekundách.

## <a name="data"></a>Údajů

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další data obsažená v této události. Další informace o tom, jak interpretovat toto pole, naleznete v tématu [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a>Úkolu

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

## <a name="event-id"></a>ID události

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo, které identifikuje typ události. Seznam identifikátorů událostí najdete v tématu [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo, které jedinečně identifikuje událost uvnitř trasování. Tato hodnota se při analýze nebo opakovaném protokolování stejného trasování několikrát nemění. Tuto hodnotu použijte k identifikaci stejné události při vícenásobné analýze nebo při opakovaném protokolování přes stejné trasování.

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec ANSI obsahující název typu události identifikovaný [ID události](#event-id).

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Návratová hodnota

Velký řetězec obsahující název typu události identifikovaný [ID události](#event-id).

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [CPUTicks](#cpu-ticks), ale ne včetně taktů procesoru, k nimž došlo v podřízených aktivitách.

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [CPUTime](#cpu-time), s tím rozdílem, že není zahrnut čas procesoru podřízených aktivit.

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách, bez zahrnutí času stráveného v podřízených aktivitách.

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů, ke kterým došlo v této aktivitě s výjimkou počtu tiků, k nimž došlo v podřízených aktivitách.

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [WallClockTimeResponsibility](#wall-clock-time-responsibility), ale nezahrnují zodpovědnost za pracovní dobu u podřízených aktivit.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), ale ne včetně časových taktů zodpovědnosti podřízených aktivit.

## <a name="process-id"></a>ID

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor procesu, ve kterém došlo k události.

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pro logický procesor, na kterém došlo k události.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota Tick zachycená v době spuštění aktivity.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota Tick zachycená v době, kdy se aktivita zastavila

## <a name="thread-id"></a>IDvlákna

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor vlákna, ve kterém došlo k události.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů za sekundu, které se použijí při vyhodnocování doby trvání měřené v taktech pro tuto událost.

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Návratová hodnota

Časová zodpovědnost za tuto aktivitu na základě hodin v nanosekundách Další informace o tom, jaká je doba zodpovědnosti za chodu, najdete v tématu [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet impulsů, který představuje příspěvek této aktivity k celkovému času na zdi. Časová zodpovědnost na zeď se liší od normálního zaškrtnutí. Časová pravítka na zdi berou v úvahu paralelismus mezi aktivitami. Dvě paralelní aktivity můžou mít dobu trvání 50 a stejnou dobu spuštění a zastavení. V takovém případě se jim přiřadí časová zodpovědnost za 25 taktů.

::: moniker-end
