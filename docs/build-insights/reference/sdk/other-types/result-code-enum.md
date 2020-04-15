---
title: RESULT_CODE výčtu
description: C++ Build Insights SDK RESULT_CODE výčtu odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323626"
---
# <a name="result_code-enum"></a>RESULT_CODE výčtu

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Výčet `RESULT_CODE` popisuje podmínky úspěchu a selhání.

## <a name="members"></a>Členové

| Name (Název) | Hodnota | Popis |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | Operace byla úspěšná. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Jedna z funkcí zpětného volání v `CALLBACK_CODE_ANALYSIS_FAILURE` [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md) vrátila hodnotu. Tato hodnota je členem [výčtu CALLBACK_CODE.](callback-code-enum.md) |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Jedna z funkcí zpětného volání v `CALLBACK_CODE_ANALYSIS_CANCEL` [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md) vrátila hodnotu. Tato hodnota je členem [výčtu CALLBACK_CODE.](callback-code-enum.md) |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | Zadané trasování vstupní události pro systém Windows (ETW) je neplatné. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | Zadané sledování výstupu ETW je neplatné. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | Struktura [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) nebyla inicializována správně. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | Struktura [RELOG_CALLBACKS](relog-callbacks-struct.md) nebyla inicializována správně. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | Nepodařilo se otevřít vstupní trasování ETW. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Při zpracování vstupního trasování ETW došlo k chybě. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Při pokusu o spuštění relace opětovného přihlášení došlo k chybě. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | Vstupní trasování ETW chybí důležité události. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Používáte C++ Sestavení Přehledy na nepodporovanou verzi systému Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | Zadaný název relace je neplatný. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Tato operace vyžaduje oprávnění správce. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Při generování identifikátoru GUID došlo k chybě. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Při pokusu o určení cesty k dočasnému adresáři došlo k chybě. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Při pokusu o vytvoření dočasného adresáře pro spuštěnou relaci trasování došlo k chybě. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Při pokusu o spuštění trasování systému došlo k chybě. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Při pokusu o spuštění trasování MSVC došlo k chybě. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Při pokusu o zastavení trasování msvcdošlo k chybě. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Při pokusu o spuštění trasování systému došlo k chybě. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Trasování bylo zastaveno, ale dočasný adresář relace trasování nebyl nalezen. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | Trasovací soubor pro trasování MSVC je zastavena nebyla nalezena. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Při slučování trasování pomocí ovládacího prvku trasování jádra došlo k chybě. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Došlo k neznámé chybě. |

::: moniker-end
