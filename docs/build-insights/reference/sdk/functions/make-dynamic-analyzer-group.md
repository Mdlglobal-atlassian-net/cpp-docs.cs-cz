---
title: MakeDynamicAnalyzerGroup
description: Reference C++ k funkci MakeDynamicAnalyzerGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332829"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeDynamicAnalyzerGroup` slouží k vytvoření dynamické skupiny analyzátorů. Členové skupiny analyzátoru obdrží události jednu od zleva doprava, dokud nebudou analyzovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parametry

\ *analyzátorů*
Vektor [IAnalyzer](../other-types/ianalyzer-class.md) ukazatelů, které jsou součástí skupiny dynamického analyzátoru. Tyto ukazatele můžou být nezpracované, `std::unique_ptr`nebo `std::shared_ptr`.

### <a name="return-value"></a>Návratová hodnota

Dynamická skupina analyzátoru. K zachycení návratové hodnoty použijte klíčové slovo **auto** .

## <a name="remarks"></a>Poznámky

Na rozdíl od statických skupin analyzátoru nemusí být členové dynamické skupiny analyzátoru v době kompilace známi. Můžete vybrat členy skupiny analyzátoru za běhu na základě vstupu programu nebo na základě jiných hodnot, které jsou v době kompilace neznámé. Na rozdíl od statických skupin analyzátoru mají ukazatele [IAnalyzer](../other-types/ianalyzer-class.md) v rámci skupiny dynamických analyzátorů polymorfní chování a volání virtuální funkce jsou odesílána správně. Tato flexibilita se dodává na náklady na potenciálně pomalejší dobu zpracování událostí. Pokud jsou všichni členové skupiny Analyzer známi v době kompilace a pokud nepotřebujete polymorfní chování, zvažte použití statické skupiny analyzátoru. Chcete-li použít statickou skupinu analyzátoru, zavolejte místo toho [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) .

Dynamickou skupinu analyzátorů lze zapouzdřit do statické skupiny analyzátorů. Provedete to tak, že adresu předáte do [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Tuto techniku použijte při předávání skupin dynamického analyzátoru funkcím, jako je například [analyzovat](analyze.md), které akceptují pouze statické skupiny analyzátorů.

::: moniker-end
