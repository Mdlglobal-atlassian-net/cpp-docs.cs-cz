---
title: Třída aktivity
description: C++ Build Insights SDK Activity odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325250"
---
# <a name="activity-class"></a>Třída aktivity

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Activity` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala události aktivity. Odkazovat na [tabulku událostí](../event-table.md) zobrazíte všechny události, které mohou odpovídat třídy. `Activity`

## <a name="syntax"></a>Syntaxe

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Poznámky

Několik členských funkcí `Activity` ve třídě vrátí počet značek. C++ Build Insights používá čítač výkonu systému Windows jako zdroj značek. Počet značek musí být použit s frekvencí značek, aby se převedl na časovou jednotku, jako jsou sekundy. Členská `TickFrequency` funkce, která je k dispozici v základní třídě [Události,](event.md) může být volána k získání frekvence značek. Stránka [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) zobrazuje příklad převodu značek na časovou jednotku.

Pokud nechcete převést značky na časové jednotky `Activity` sami, třída poskytuje členské funkce, které vracejí časové hodnoty v nanosekundách. Pomocí standardní knihovny `chrono` Jazyka C++ je můžete převést na jiné časové jednotky.

## <a name="members"></a>Členové

Spolu se svými členy [Event](event.md) zděděnými `Activity` ze základní třídy Event obsahuje třída následující členy:

### <a name="constructor"></a>Konstruktor

[Činnosti](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[Čas procesoru](#cpu-time)\
[Doba trvání](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[Výhradní WallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimerazítko](#start-timestamp)\
[StopTimerazítko](#stop-timestamp)\
[WallClockTimeOdpovědnost](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a>Činnosti

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Jakákoli událost aktivity.

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

## <a name="duration"></a><a name="duration"></a>Doba trvání

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

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
