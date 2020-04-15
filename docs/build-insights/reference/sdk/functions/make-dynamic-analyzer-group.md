---
title: MakeDynamicAnalyzerGroup
description: C++ Build Insights SDK MakeDynamicAnalyzerGroup odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323960"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Tato `MakeDynamicAnalyzerGroup` funkce se používá k vytvoření skupiny dynamických analyzátorů. Členové skupiny analyzátorů přijímají události jeden po druhém zleva doprava, dokud nebudou analyzovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parametry

*Analyzátory*\
Vektor ukazatelů [IAnalyzer](../other-types/ianalyzer-class.md) zahrnutých ve skupině dynamických analyzátorů. Tyto ukazatele mohou být `std::unique_ptr`nezpracované nebo `std::shared_ptr`.

### <a name="return-value"></a>Návratová hodnota

Skupina dynamických analyzátorů. Pomocí **klíčového** slova auto zachyťte vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Na rozdíl od skupin statických analyzátorů nemusí být členové skupiny dynamického analyzátoru známi v době kompilace. Můžete zvolit členy skupiny analyzátoru za běhu na základě vstupu programu nebo na základě jiných hodnot, které nejsou v době kompilace známy. Na rozdíl od skupin statických analyzátorů ukazatele [IAnalyzer](../other-types/ianalyzer-class.md) v rámci skupiny dynamických analyzátorů mají polymorfní chování a volání virtuálních funkcí jsou odesílána správně. Tato flexibilita přichází na úkor pravděpodobně pomalejší čas zpracování událostí. Pokud jsou v době kompilace známy všechny členy skupiny analyzátorů a pokud nepotřebujete polymorfní chování, zvažte použití statické skupiny analyzátorů. Chcete-li použít statickou skupinu analyzátorů, zavolejte místo toho [MakeStaticAnalyzerGroup.](make-static-analyzer-group.md)

Skupinu dynamických analyzátorů lze zapouzdřit uvnitř statické skupiny analyzátorů. To se provádí předáním jeho adresu [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Tuto techniku použijte pro předávání dynamických skupin analyzátorů funkcím, jako je [analyzovat](analyze.md), které přijímají pouze skupiny statických analyzátorů.

::: moniker-end
