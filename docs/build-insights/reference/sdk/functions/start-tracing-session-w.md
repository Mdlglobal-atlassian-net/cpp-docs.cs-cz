---
title: StartTracingSessionW
description: Reference C++ k funkci StartTracingSessionW sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 072b02166f2841e6d210306ef75c9fc64fea9778
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332647"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StartTracingSessionW` spustí relaci trasování. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>Parametry

*název_relace*\
Název relace trasování, která se má spustit. Použijte stejný název při volání [StopTracingSessionW](stop-tracing-session-w.md)nebo jakékoli jiné funkce stop Trace.

*možnosti*\
Ukazatel na objekt [TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) . Pomocí tohoto objektu vyberte, které události by měly být shromažďovány trasovací relací.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
