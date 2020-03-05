---
title: StartTracingSession
description: Reference C++ k funkci StartTracingSession sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de9d46b4a684d66bf01f76e7ea753694cf40d2cd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332619"
---
# <a name="starttracingsession"></a>StartTracingSession

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StartTracingSession` spustí relaci trasování. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
RESULT_CODE StartTracingSession(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS& options);

RESULT_CODE StartTracingSession(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS& options);
```

### <a name="parameters"></a>Parametry

*název_relace*\
Název relace trasování, která se má spustit. Při volání [StopTracingSession](stop-tracing-session.md) nebo jakékoli jiné funkce stop Trace použijte stejný název.

*možnosti*\
Ukazatel na objekt [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) . Pomocí tohoto objektu vyberte, které události by měly být shromažďovány trasovací relací.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
