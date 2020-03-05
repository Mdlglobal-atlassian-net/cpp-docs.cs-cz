---
title: Event – třída
description: Odkaz C++ na třídu události Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333396"
---
# <a name="event-class"></a>Event – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Event` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování libovolné události.

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

[Události](#entity)

### <a name="functions"></a>Functions

[Data](#data)
[ID události](#event-id)\
[EventInstanceId](#event-instance-id)\
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[Id_procesu](#process-id)\
[ProcessorIndex](#processor-index)\
[Idvlákna](#thread-id)\
[TickFrequency](#tick-frequency)\
[Časové razítko](#timestamp)

## <a name="entity"></a>Událostí

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Jakákoli událost.

## <a name="data"></a>Údajů

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další data obsažená v této události. Další informace o tom, jak interpretovat toto pole, naleznete v tématu [EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Velký řetězec obsahující název události identifikovaný [ID události](#event-id).

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

## <a name="timestamp"></a>Časové razítko

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je událost aktivitou, tato funkce vrátí hodnotu Tick zachycenou v době spuštění aktivity. Pro jednoduchou událost Tato funkce vrací hodnotu Tick zachycenou v době, kdy došlo k události.

::: moniker-end
