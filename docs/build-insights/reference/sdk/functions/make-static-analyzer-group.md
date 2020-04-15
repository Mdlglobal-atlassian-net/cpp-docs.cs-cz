---
title: Skupina MakeStaticAnalyzerGroup
description: C++ Build Insights SDK MakeStaticAnalyzerGroup odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323933"
---
# <a name="makestaticanalyzergroup"></a>Skupina MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeStaticAnalyzerGroup` se používá k vytvoření statické skupiny analyzátorů, která může být předána funkcím, jako je [Analyzovat](analyze.md) nebo [Vyvolat](relog.md). Členové skupiny analyzátorů přijímají události jeden po druhém zleva doprava, dokud nebudou analyzovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parametry

*TAnalyzerPtrs*\
Tento parametr je vždy odvodit.

*Analyzátory*\
Balíček parametrů ukazatelů [IAnalyzer](../other-types/ianalyzer-class.md) zahrnutých ve skupině statických analyzátorů. Tyto ukazatele mohou být `std::unique_ptr`nezpracované nebo `std::shared_ptr`.

### <a name="return-value"></a>Návratová hodnota

Skupina statických analyzátorů. Pomocí **klíčového** slova auto zachyťte vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Na rozdíl od skupin dynamických analyzátorů musí být členové skupiny statických analyzátorů známi v době kompilace. Skupina statického analyzátoru navíc obsahuje ukazatele [IAnalyzer,](../other-types/ianalyzer-class.md) které nemají polymorfní chování. Při použití statické analyzátor skupiny k analýze trasování trasování událostí pro `IAnalyzer` Windows (ETW), volání rozhraní vždy vyřešit objekt přímo ukázal člen skupiny analyzátoru. Tato ztráta flexibility přichází s možností rychlejšího zpracování událostí. Pokud členové skupiny analyzátoru nelze znát v době kompilace nebo pokud požadujete `IAnalyzer` polymorfní chování na ukazatelích, zvažte použití skupiny dynamického analyzátoru. Chcete-li použít skupinu dynamických analyzátorů, zavolejte místo toho [makedynamicanalyzergroup.](make-static-analyzer-group.md)

::: moniker-end
