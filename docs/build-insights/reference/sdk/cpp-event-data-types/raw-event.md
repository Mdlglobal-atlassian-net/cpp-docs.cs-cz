---
title: Třída RawEvent
description: Odkaz na třídu C++ Build Insights SDK RawEvent.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324373"
---
# <a name="rawevent-class"></a>Třída RawEvent

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `RawEvent` se používá k reprezentaci obecné události v [EventStack](event-stack.md).

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

Několik členských funkcí `RawEvent` ve třídě vrátí počet značek. C++ Build Insights používá čítač výkonu systému Windows jako zdroj značek. Počet značek musí být použit s frekvencí značek, aby se převedl na časovou jednotku, jako jsou sekundy. Členská `TickFrequency` funkce může být volána k získání frekvence klíšťat. Příklad, jak převést značky na časovou jednotku, najdete na stránce [EVENT_DATA.](../c-event-data-types/event-data-struct.md#tick-conversion-example)

Pokud nechcete převést značky sami, `RawEvent` třída poskytuje členské funkce, které vracejí časové hodnoty v nanosekundách. Pomocí standardní knihovny `chrono` Jazyka C++ můžete převést nanosekundy do jiných časových jednotek.

## <a name="members"></a>Členové

### <a name="constructor"></a>Konstruktor

[Akce RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[Čas procesoru](#cpu-time)\
[Dat](#data)\
[Doba trvání](#duration)\
[Název události EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[Název_události](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[Výhradní WallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Processid](#process-id)\
[Index procesoru](#processor-index)\
[StartTimerazítko](#start-timestamp)\
[StopTimerazítko](#stop-timestamp)\
[ThreadId](#thread-id)\
[Frekvence zaškrtnutí](#tick-frequency)\
[WallClockTimeOdpovědnost](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>Akce RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parametry

*Událost*\
Data události

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek procesoru, ke kterým došlo během této aktivity. Klíště procesoru se liší od běžného zaškrtnutí. Značky procesoru se počítají pouze v případě, že procesor provádí kód v aktivitě. Klíšťata procesoru se nepočítají, když je vlákno přidružené k aktivitě v režimu spánku.

## <a name="cputime"></a><a name="cpu-time"></a>Čas procesoru

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba, po kterou procesor prováděl kód uvnitř této aktivity. Tato hodnota může být vyšší než doba trvání aktivity, pokud podřízené aktivity jsou prováděny v samostatných vláknech. Hodnota je vrácena v nanosekundách.

## <a name="data"></a><a name="data"></a>Dat

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další data obsažená v této události. Další informace o interpretaci tohoto pole naleznete v [tématu EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a>Doba trvání

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

## <a name="eventid"></a><a name="event-id"></a>Eventid

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo, které identifikuje typ události. Seznam identifikátorů událostí naleznete [v tématu EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>Id instance události

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo, které jednoznačně identifikuje událost uvnitř trasování. Tato hodnota se nezmění při analýze nebo opětovném přihlášení stejné trasování vícekrát. Tuto hodnotu použijte k identifikaci stejné události ve více analýzách nebo opětovném zaprotokolování průchodů přes stejné trasování.

## <a name="eventname"></a><a name="event-name"></a>Eventname

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec ANSI obsahující název typu události identifikovaného [eventid](#event-id).

## <a name="eventwidename"></a><a name="event-wide-name"></a>Název_události

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Návratová hodnota

Široký řetězec obsahující název typu události identifikovaného [EventId](#event-id).

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [CPUTicks](#cpu-ticks), ale ne zahrnuje cpu značky, ke kterým došlo v podřízené aktivity.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [CPUTime](#cpu-time), s tím rozdílem, že čas procesoru podřízených aktivit není zahrnuta.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách, bez množství času stráveného v podřízených aktivitách.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek, ke kterým došlo v této aktivitě, s výjimkou počtu značek, ke kterým došlo v podřízených aktivitách.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>Výhradní WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [WallClockTimeResponsibility](#wall-clock-time-responsibility), ale ne zahrnuje zeď-hodiny čas odpovědnosti podřízených aktivit.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Stejné jako [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), ale ne zahrnuje zeď hodiny čas odpovědnosti tiká podřízené aktivity.

## <a name="processid"></a><a name="process-id"></a>Processid

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor pro proces, ve kterém došlo k události.

## <a name="processorindex"></a><a name="processor-index"></a>Index procesoru

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pro logický procesor, na kterém došlo k události.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimerazítko

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota značky zachycená v době zahájení aktivity.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimerazítko

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota značky zachycená v době, kdy byla aktivita zastavena.

## <a name="threadid"></a><a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor vlákna, ve kterém došlo k události.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Frekvence zaškrtnutí

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek za sekundu použít při hodnocení trvání měřeno v značek pro tuto událost.

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>WallClockTimeOdpovědnost

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Návratová hodnota

Odpovědnost za tuto aktivitu v nanosekundách. Další informace o tom, co wall-clock čas odpovědnost znamená, naleznete v [tématu WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet značek, který představuje příspěvek této aktivity k celkovému času nástěnných hodin. Klíště odpovědnosti za čas na zdi se liší od běžného klíštěte. Nástěnné hodiny čas odpovědnost i tiky vzít v úvahu paralelismus mezi aktivitami. Dvě paralelní aktivity mohou mít dobu trvání 50 značek a stejný čas zahájení a zastavení. V tomto případě oba získat přiřazena zeď-hodiny čas odpovědnosti 25 značek.

::: moniker-end
