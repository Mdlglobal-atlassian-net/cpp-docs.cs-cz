---
title: Activity – Třída
description: Odkaz C++ na třídu aktivity Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333557"
---
# <a name="activity-class"></a>Activity – Třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Activity` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho k vyhledání události aktivity. Chcete-li zobrazit všechny události, které mohou být porovnány třídou `Activity`, přečtěte si téma [tabulka událostí](../event-table.md) .

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

Několik členských funkcí ve třídě `Activity` vrací počet impulsů. C++Build Insights používá čítač výkonu Windows jako zdroj taktů. Aby bylo možné provést převod na časovou jednotku, například sekund, je nutné použít počet impulsů s frekvencí Tick. Členská funkce `TickFrequency`, která je k dispozici v základní třídě [Event](event.md) , může být volána pro získání frekvence Tick. Stránka [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) ukazuje příklad převodu tiků na časovou jednotku.

Pokud nechcete převádět osové hodnoty na časové jednotky sami, třída `Activity` poskytne členské funkce, které vracejí hodnoty času v nanosekundách. Pomocí standardní C++ knihovny `chrono` převeďte je na jiné časové jednotky.

## <a name="members"></a>Členové

Spolu s členy zděděnými ze základní třídy [Event](event.md) třída `Activity` obsahuje následující členy:

### <a name="constructor"></a>Konstruktor

[Aktivita](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
\ [doby trvání](#duration)
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>Akce

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Jakákoli událost aktivity.

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

## <a name="duration"></a>Úkolu

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Návratová hodnota

Doba trvání aktivity v nanosekundách.

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

Počet impulsů, který představuje příspěvek této aktivity k celkovému času na zdi. Časová zodpovědnost na zeď se liší od normálního zaškrtnutí. Časová pravítka na zdi berou v úvahu paralelismus mezi aktivitami. Dvě paralelní aktivity můžou mít dobu trvání 50 a stejný čas spuštění a zastavení. V takovém případě se jim přiřadí časová zodpovědnost za 25 taktů.

::: moniker-end
