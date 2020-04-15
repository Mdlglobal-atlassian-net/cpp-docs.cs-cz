---
title: Třída události
description: Odkaz na třídu SDK s c++ sestavení ms.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324966"
---
# <a name="event-class"></a>Třída události

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Event` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala jakékoli události.

## <a name="syntax"></a>Syntaxe

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

[Událost](#entity)

### <a name="functions"></a>Functions

[Id](#data)
[události dat](#event-id)\
[Id instance události](#event-instance-id)\
[Eventname](#event-name)\
[Název_události](#event-wide-name)\
[Processid](#process-id)\
[Index procesoru](#processor-index)\
[ThreadId](#thread-id)\
[Frekvence zaškrtnutí](#tick-frequency)\
[Časové razítko](#timestamp)

## <a name="event"></a><a name="entity"></a>Událost

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
V každém případě.

## <a name="data"></a><a name="data"></a>Dat

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další data obsažená v této události. Další informace o interpretaci tohoto pole naleznete v [tématu EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Široký řetězec obsahující název události identifikované [EventId](#event-id).

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

## <a name="timestamp"></a><a name="timestamp"></a>Časové razítko

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je událost aktivitou, vrátí tato funkce hodnotu značky zachycenou v době zahájení aktivity. Pro jednoduchou událost vrátí tato funkce hodnotu značky zachycenou v době, kdy k události došlo.

::: moniker-end
