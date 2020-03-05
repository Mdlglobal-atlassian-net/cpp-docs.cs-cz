---
title: StopAndRelogTracingSessionA
description: Reference C++ k funkci StopAndRelogTracingSessionA sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c9fe2ea47b378565d3ce9785b6f4cc3e541ebe80
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332703"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndRelogTracingSessionA` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace, která se znovu zaznamená, pak okamžitě začne používat dočasný soubor jako vstup. Konečné přeprotokolované trasování vytvořené relací znovu protokolování je uloženo v souboru určeném volajícím. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>Parametry

*název_relace*\
Název relace trasování, která se má zastavit. Použijte stejný název relace jako ten předaný do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Soubor, ve kterém se má zapsat přeprotokolované trasování vytvořené relací znovu protokolování.

\ *statistiky*
Ukazatel na objekt [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . před vrácením `StopAndRelogTracingSessionA` zapisuje statistiky shromažďování trasování v tomto objektu.

*analysisDescriptor*\
Ukazatel na objekt [RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Pomocí tohoto objektu můžete nakonfigurovat relaci znovu protokolovaných protokolů spuštěnou v `StopAndRelogTracingSessionA`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
