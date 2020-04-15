---
title: EVENT_DATA struktura
description: C++ Sestavení Insights SDK EVENT_DATA struktura odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325595"
---
# <a name="event_data-structure"></a>EVENT_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_DATA` popisuje událost přijatou z analýzy nebo opětovného přihlášení relace. Tyto relace jsou spuštěny voláním [funkce Analyzovat](../functions/analyze.md), [AnalyzovatA](../functions/analyze-a.md), [AnalyzovatW](../functions/analyze-w.md), [Relog](../functions/relog.md), [RelogA](../functions/relog-a.md)nebo [RelogW.](../functions/relog-w.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `EventId` | Číslo, které identifikuje událost. Seznam identifikátorů událostí naleznete [v tématu EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Číslo, které jednoznačně identifikuje aktuální událost uvnitř trasování. Tato hodnota se nezmění při analýze nebo opětovném přihlášení stejné trasování vícekrát. Toto pole slouží k identifikaci stejné události ve více analýzách nebo opětovném zaprotokolování průchodů přes stejné trasování. |
| `TickFrequency` | Počet klíšťat za sekundu, které se mají použít při hodnocení doby trvání měřené v klíšťacích. |
| `StartTimestamp` | Pokud je událostí *aktivita*, je toto pole nastaveno na hodnotu značky zachycenou v době zahájení aktivity. Pokud je tato událost *jednoduchá událost*, je toto pole nastaveno na hodnotu značky zachycenou v době, kdy k události došlo. |
| `StopTimestamp` | Pokud je událostí *aktivita*, je toto pole nastaveno na hodnotu značky zachycenou v době, kdy byla aktivita zastavena. Pokud pro tuto aktivitu ještě nebyla přijata událost stop, je toto pole nastaveno na nulu. Pokud je tato událost *jednoduchá událost*, je toto pole nastaveno na nulu. |
| `ExclusiveDurationTicks` | Pokud je tato událost *aktivita*, toto pole je nastaveno na počet značek, ke kterým došlo přímo v této aktivitě. Počet značek, ke kterým došlo v podřízené aktivity jsou vyloučeny. Toto pole je nastaveno na *nulu*pro jednoduché události . |
| `CPUTicks` | Pokud je tato událost *aktivita*, toto pole je nastavena na počet značek procesoru, ke kterým došlo během této aktivity. Klíště procesoru se liší od běžného zaškrtnutí. Značky procesoru se počítají pouze v případě, že procesor provádí kód v aktivitě. Klíšťata procesoru se nepočítají, když je vlákno přidružené k aktivitě v režimu spánku. Toto pole je nastaveno na *nulu*pro jednoduché události . |
| `ExclusiveCPUTicks` | Toto pole má `CPUTicks`stejný význam jako , kromě toho, že neobsahuje značky procesoru, ke kterým došlo v podřízených aktivitách. Toto pole je nastaveno na *nulu*pro jednoduché události . |
| `WallClockTimeResponsibilityTicks` | Pokud je tato událost *Aktivita*, toto pole je nastaveno na počet značek, který představuje příspěvek této aktivity k celkovému času nástěnných hodin. Klíště odpovědnosti za čas na zdi se liší od běžného klíštěte. Nástěnné hodiny čas odpovědnost i tiky vzít v úvahu paralelismus mezi aktivitami. Například dvě paralelní aktivity mohou mít dobu trvání 50 značek a stejný čas zahájení a zastavení. V tomto případě bude oběma přidělena odpovědnost za čas na zeď 25 značek. Toto pole je nastaveno na *nulu*pro jednoduché události . |
| `ExclusiveWallClockTimeResponsibilityTicks` | Toto pole má `WallClockTimeResponsibilityTicks`stejný význam jako , s tím rozdílem, že neobsahuje zdi hodiny čas odpovědnost i pro děti aktivity. Toto pole je nastaveno na *nulu*pro jednoduché události . |
| `Data` | Odkazuje na další data uložená v události. Typ dat, na která je odkazováno, se liší v závislosti na `EventId` poli. |
| `ProcessId` | Identifikátor pro proces, ve kterém došlo k události. |
| `ThreadId` | Identifikátor vlákna, ve kterém došlo k události. |
| `ProcessorIndex` | Číslo procesoru s nulovým indexem, na kterém došlo k události. |
| `EventName` | Řetězec ANSI obsahující název entity identifikované `EventId`. |
| `EventWideName` | Široký řetězec obsahující název entity identifikované `EventId`. |

## <a name="remarks"></a>Poznámky

Mnoho polí `EVENT_DATA` v obsahují počty značek. C++ Přehledy sestavení používá čítač výkonu okna jako zdroj značek. Počítání značek musí být `TickFrequency` použito s polem, aby bylo převedeno na vhodnou časovou jednotku, například sekundy. Podívejte se na následující příklad pro provedení tohoto převodu. `EVENT_DATA`neobsahuje pole pro pravidelný počet značek aktivity. Chcete-li získat tuto `StartTimestamp` `StopTimestamp`hodnotu, odečíst od . `EVENT_DATA`je struktura, která je určena pro uživatele rozhraní C API. Pro uživatele rozhraní API jazyka C++ třídy jako [Událost](../cpp-event-data-types/event.md) provést převody času automaticky.

Hodnota `EVENT_DATA` `Data` pole závisí na hodnotě `EventId` jeho pole. Hodnota `Data` je popsána v následující tabulce. Některé identifikátory entit mohou v následující tabulce chybět. V tomto případě `Data` je pole `nullptr` nastaveno na hodnotu nebo nulu.

| `EventId`Hodnotu | Typ, na který se ukazuje`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Příklad převodu značek

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
