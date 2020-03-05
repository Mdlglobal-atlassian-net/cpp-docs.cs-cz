---
title: MakeStaticReloggerGroup
description: Reference C++ k funkci MakeStaticReloggerGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332808"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeStaticReloggerGroup` slouží k vytvoření skupiny statického přeprotokolovacího nástroje, kterou lze předat funkcím, jako je například [relog](relog.md). Členové skupiny reprotokolovacích nástrojů obdrží události jeden od zleva doprava, dokud nebudou zpracovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parametry

*TReloggerPtrs*\
Tento parametr je vždy odvozený.

\ *přeprotokolovacích* nástrojů
Sada parametrů ukazatelů [IRelogger](../other-types/irelogger-class.md) , která je součástí skupiny statických přeprotokolovacích souborů. Tyto ukazatele můžou být nezpracované, `std::unique_ptr`nebo `std::shared_ptr`. Ukazatele [IAnalyzer](../other-types/ianalyzer-class.md) se také považují za `IRelogger` ukazatelé z důvodu vztahu dědičnosti.

### <a name="return-value"></a>Návratová hodnota

Skupina statických přeprotokolovacích souborů. K zachycení návratové hodnoty použijte klíčové slovo **auto** .

## <a name="remarks"></a>Poznámky

Na rozdíl od dynamických skupin přeprotokolovacích souborů musí být členy skupiny statických protokolovacích nástrojů známo v době kompilace. Kromě toho skupina statických přeprotokolovacích souborů obsahuje ukazatele [IRelogger](../other-types/irelogger-class.md) , které nemají polymorfní chování. Při použití skupiny statického přeprotokolovacího nástroje k analýze trasování událostí pro Windows (ETW) se volání rozhraní `IRelogger` vždy přeloží na objekt přímo, na který odkazuje člen skupiny reprotokolovacích nástrojů. Tato ztráta flexibility je dodávána s možností rychlejšího zpracování událostí. Pokud členy skupiny reprotokolovacích souborů nelze znát v době kompilace, nebo pokud vyžadujete polymorfní chování ukazatelů `IRelogger`, zvažte použití dynamické skupiny reprotokolovacích nástrojů. Můžete použít dynamickou skupinu přeprotokolovacích souborů voláním [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) místo.

::: moniker-end
