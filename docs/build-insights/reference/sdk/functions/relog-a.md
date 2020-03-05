---
title: Relog
description: Odkaz C++ na funkci pro sestavení Insights SDK relog.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4427aa0ac85e34bfb9d569913a8ccf6ab264f52
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332731"
---
# <a name="reloga"></a>Relog

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `RelogA` slouží ke čtení událostí MSVC z trasování událostí pro Windows (ETW) a jejich zápis do nového upraveného trasování ETW.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*outputLogFile*\
Soubor, do kterého mají být zapsány nové události.

*relogDescriptor*\
Ukazatel na objekt [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md) . Pomocí tohoto objektu můžete nakonfigurovat relaci přehlašování.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
