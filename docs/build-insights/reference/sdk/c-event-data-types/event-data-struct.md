---
title: Struktura EVENT_DATA
description: Odkaz C++ na strukturu EVENT_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417444"
---
# <a name="event_data-structure"></a>Struktura EVENT_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_DATA` popisuje událost přijatou z relace analýzy nebo nové protokolování. Tyto relace se spustí voláním funkce [analyzovat](../functions/analyze.md), [analyzovat](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [relog](../functions/relog.md), [relog](../functions/relog-a.md)nebo [RelogW](../functions/relog-w.md) .

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
| `EventId` | Číslo identifikující událost. Seznam identifikátorů událostí najdete v tématu [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Číslo, které jedinečně identifikuje aktuální událost v rámci trasování. Tato hodnota se při analýze nebo opakovaném protokolování stejného trasování několikrát nemění. Pomocí tohoto pole můžete identifikovat stejnou událost při vícenásobné analýze nebo při opakovaném protokolování přes stejné trasování. |
| `TickFrequency` | Počet taktů za sekundu, které se použijí při vyhodnocování doby trvání měřené v taktech. |
| `StartTimestamp` | Pokud je událost *aktivitou*, toto pole je nastaveno na hodnotu Tick zachycenou v době spuštění aktivity. Pokud je tato událost *Jednoduchá událost*, toto pole je nastaveno na hodnotu Tick zachycenou v době, kdy došlo k události. |
| `StopTimestamp` | Pokud je událost *aktivitou*, toto pole je nastaveno na hodnotu Tick zachycenou v době, kdy byla aktivita zastavena. Pokud pro tuto aktivitu ještě nebyla přijata událost stop, je toto pole nastaveno na hodnotu nula. Pokud je tato událost *Jednoduchá událost*, je toto pole nastaveno na hodnotu nula. |
| `ExclusiveDurationTicks` | Pokud je tato událost *aktivitou*, toto pole je nastaveno na počet tiků, k nimž došlo přímo v této aktivitě. Počet tiků, k nimž došlo v podřízené aktivitě, je vyloučený. Pro *jednoduché události*je toto pole nastaveno na hodnotu nula. |
| `CPUTicks` | Pokud je tato událost *aktivitou*, bude toto pole nastaveno na počet cyklů procesoru, které během této aktivity nastaly. Takt procesoru se liší od normálního zaškrtnutí. Takty procesoru se počítají jenom v případě, že CPU spouští kód v aktivitě. Cykly procesoru se nepočítají, pokud je vlákno přidružené k aktivitě v režimu spánku. Pro *jednoduché události*je toto pole nastaveno na hodnotu nula. |
| `ExclusiveCPUTicks` | Toto pole má stejný význam jako `CPUTicks`, s tím rozdílem, že nezahrnuje takty procesoru, k nimž došlo v aktivitách podřízeného objektu. Pro *jednoduché události*je toto pole nastaveno na hodnotu nula. |
| `WallClockTimeResponsibilityTicks` | Pokud je tato událost *aktivitou*, bude toto pole nastaveno na počet impulsů, který představuje příspěvek této aktivity na celkový čas na hodinách. Časová zodpovědnost na zeď se liší od normálního zaškrtnutí. Časová pravítka na zdi berou v úvahu paralelismus mezi aktivitami. Například dvě paralelní aktivity mohou mít dobu trvání 50 a stejnou dobu spuštění a zastavení. V takovém případě se jim přiřadí časová zodpovědnost za 25 taktů. Pro *jednoduché události*je toto pole nastaveno na hodnotu nula. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Toto pole má stejný význam jako `WallClockTimeResponsibilityTicks`, s tím rozdílem, že nezahrnuje časové takty u podřízených aktivit. Pro *jednoduché události*je toto pole nastaveno na hodnotu nula. |
| `Data` | Odkazuje na další data uložená v události. Typ dat, na které se odkazuje, se liší v závislosti na poli `EventId`. |
| `ProcessId` | Identifikátor procesu, ve kterém došlo k události. |
| `ThreadId` | Identifikátor vlákna, ve kterém došlo k události. |
| `ProcessorIndex` | Nulové číslo procesoru, na kterém došlo k události. |
| `EventName` | Řetězec ANSI obsahující název entity identifikované `EventId`. |
| `EventWideName` | Velký řetězec obsahující název entity identifikované `EventId`. |

## <a name="remarks"></a>Poznámky

Mnoho polí v `EVENT_DATA` obsahuje počty impulsů. C++Přehledy sestavení využívají čítač výkonu okna jako zdroj taktů. Aby se pole `TickFrequency` převedlo na příslušnou časovou jednotku, například sekund, musí se použít počet impulsů. Projděte si následující příklad pro provádění tohoto převodu. `EVENT_DATA` neobsahuje pole pro běžný počet impulsů aktivity. Chcete-li získat tuto hodnotu, odčítání `StartTimestamp` od `StopTimestamp`. `EVENT_DATA` je struktura, která je určena pro použití uživateli rozhraní API jazyka C. Pro C++ uživatele rozhraní API třídy, jako je například [událost](../cpp-event-data-types/event.md) převody času, jsou automaticky.

Hodnota pole `EVENT_DATA` `Data` závisí na hodnotě jeho pole `EventId`. Hodnota `Data` je popsána v následující tabulce. V tabulce níže můžou chybět nějaké identifikátory entit. V tomto případě je pole `Data` nastaveno na hodnotu `nullptr` nebo nula.

| hodnota `EventId` | Typ, na který odkazuje `Data` |
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

## <a name="tick-conversion-example"></a>Příklad převodu osové značky

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
