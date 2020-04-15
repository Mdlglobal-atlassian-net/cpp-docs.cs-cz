---
title: StopAndRelogTracingSessionW
description: C++ Build Insights SDK StopAndRelogTracingSessionW odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c542ba8f313f30cf5adb069dd02cf3db29ffc532
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323693"
---
# <a name="stopandrelogtracingsessionw"></a>StopAndRelogTracingSessionW

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndRelogTracingSessionW` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace opětovného přihlášení je pak okamžitě začít používat dočasný soubor jako vstup. Konečné relogged trasování vytvořené relogging relace je uložen v souboru určeném volajícím. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopAndRelogTracingSessionW(
    const wchar_t*              sessionName,
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parametry

*Název_relace*\
Název relace trasování zastavit. Použijte stejný název relace jako název předané [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Soubor, ve kterém chcete zapsat relogged trasování vytvořené relogging relace.

*Statistiky*\
Ukazatel na [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) objekt. `StopAndRelogTracingSessionW`zapíše statistiky shromažďování trasování v tomto objektu před vrácením.

*analysisDescriptor*\
Ukazatel na [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) objekt. Tento objekt slouží ke konfiguraci relace opětovného správě, která je spuštěna aplikací `StopAndRelogTracingSessionW`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
