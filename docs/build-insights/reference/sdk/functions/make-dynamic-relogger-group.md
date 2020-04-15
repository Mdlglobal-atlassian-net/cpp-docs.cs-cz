---
title: MakeDynamicReloggerSkupina
description: C++ Build Insights SDK MakeDynamicReloggerGroup odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323956"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerSkupina

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeDynamicReloggerGroup` se používá k vytvoření dynamické skupiny relogger. Členové skupiny relogger přijímat události jeden po druhém zleva doprava, dokud všechny události v trasování byly zpracovány.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parametry

*reloggery*\
Vektor [ukazatelů IRelogger](../other-types/irelogger-class.md) zahrnutých ve skupině dynamického reloggeru. Tyto ukazatele mohou být `std::unique_ptr`nezpracované nebo `std::shared_ptr`. [Ukazatele IAnalyzer](../other-types/ianalyzer-class.md) jsou `IRelogger` také považovány za ukazatele z důvodu vztahu dědičnosti.

### <a name="return-value"></a>Návratová hodnota

Dynamická skupina reloggerů. Pomocí **klíčového** slova auto zachyťte vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Na rozdíl od statických relogger skupiny, členové dynamické skupiny relogger nemusí být známy v době kompilace. Můžete zvolit členy skupiny relogger za běhu na základě vstupu programu nebo na základě jiných hodnot, které nejsou známy v době kompilace. Na rozdíl od statických relogger [skupiny IRelogger](../other-types/irelogger-class.md) ukazatele v rámci dynamické skupiny relogger mají polymorfní chování a virtuální funkce volání jsou odesílány správně. Tato flexibilita přichází na úkor pravděpodobně pomalejší čas zpracování událostí. Když jsou všichni členové skupiny reloggeru známi v době kompilace a pokud nepotřebujete polymorfní chování, zvažte použití statické skupiny reloggeru. Chcete-li použít statickou skupinu relogger, volání [MakeStaticReloggerGroup](make-static-relogger-group.md) místo.

Dynamická skupina reloggeru může být zapouzdřena uvnitř statické skupiny relogger. Předáte jeho adresu [MakeStaticReloggerGroup](make-static-relogger-group.md). Tento postup použijte pro předávání dynamických skupin reloggeru do funkcí, jako je [Relog](relog.md), které přijímají pouze statické skupiny reloggerů.

::: moniker-end
