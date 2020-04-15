---
title: MakestaticReloggerSkupina
description: C++ Build Insights SDK MakestaticreloggerGroup odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323916"
---
# <a name="makestaticreloggergroup"></a>MakestaticReloggerSkupina

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeStaticReloggerGroup` se používá k vytvoření statické skupiny reloggeru, která může být předána funkcím, jako je [Relog](relog.md). Členové skupiny relogger přijímat události jeden po druhém zleva doprava, dokud všechny události v trasování byly zpracovány.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parametry

*TReloggerPtrs*\
Tento parametr je vždy odvodit.

*reloggery*\
Balíček parametrů [ukazatelů IRelogger,](../other-types/irelogger-class.md) který je součástí statické skupiny relogger. Tyto ukazatele mohou být `std::unique_ptr`nezpracované nebo `std::shared_ptr`. [Ukazatele IAnalyzer](../other-types/ianalyzer-class.md) jsou `IRelogger` také považovány za ukazatele z důvodu vztahu dědičnosti.

### <a name="return-value"></a>Návratová hodnota

Statická skupina reloggerů. Pomocí **klíčového** slova auto zachyťte vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Na rozdíl od dynamických relogger skupiny, musí být členové statické relogger skupiny známé v době kompilace. Navíc statické relogger skupina obsahuje [ukazatele IRelogger,](../other-types/irelogger-class.md) které nemají polymorfní chování. Při použití statické relogger skupiny analyzovat trasování trasování událostí pro Windows `IRelogger` (ETW), volání rozhraní vždy vyřešit objekt přímo ukázal člen skupiny relogger. Tato ztráta flexibility přichází s možností rychlejšího zpracování událostí. Pokud členové skupiny relogger nelze znát v době kompilace, nebo pokud požadujete `IRelogger` polymorfní chování na ukazatele, zvažte použití dynamické skupiny relogger. Můžete použít dynamickou skupinu relogger voláním [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) místo.

::: moniker-end
