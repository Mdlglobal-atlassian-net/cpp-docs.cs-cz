---
title: MakeStaticAnalyzerGroup
description: Reference C++ k funkci MakeStaticAnalyzerGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332815"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeStaticAnalyzerGroup` slouží k vytvoření skupiny statických analýz, které lze předat funkcím, jako je například [Analýza](analyze.md) nebo [relog](relog.md). Členové skupiny analyzátoru obdrží události jednu od zleva doprava, dokud nebudou analyzovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parametry

*TAnalyzerPtrs*\
Tento parametr je vždy odvozený.

\ *analyzátorů*
Sada parametrů [IAnalyzer](../other-types/ianalyzer-class.md) ukazatelů obsažená ve skupině statických analýz Tyto ukazatele můžou být nezpracované, `std::unique_ptr`nebo `std::shared_ptr`.

### <a name="return-value"></a>Návratová hodnota

Statická skupina analyzátoru. K zachycení návratové hodnoty použijte klíčové slovo **auto** .

## <a name="remarks"></a>Poznámky

Na rozdíl od dynamických skupin analyzátoru musí být členy statické skupiny analyzátoru známy v době kompilace. Kromě toho skupina statických analýz obsahuje ukazatele [IAnalyzer](../other-types/ianalyzer-class.md) , které nemají polymorfní chování. Při použití statické skupiny analyzátoru k analýze trasování událostí pro Windows (ETW) se volání rozhraní `IAnalyzer` vždy přeloží na objekt přímo odkazoval na člen skupiny analyzátoru. Tato ztráta flexibility je dodávána s možností rychlejšího zpracování událostí. Pokud členy skupiny analyzátorů nelze znát v době kompilace, nebo pokud vyžadujete na ukazatelích `IAnalyzer` polymorfní chování, zvažte použití dynamické skupiny analyzátoru. Chcete-li použít dynamickou skupinu analyzátoru, zavolejte místo toho [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) .

::: moniker-end
