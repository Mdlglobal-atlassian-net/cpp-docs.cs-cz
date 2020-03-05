---
title: MakeDynamicReloggerGroup
description: Reference C++ k funkci MakeDynamicReloggerGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332822"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MakeDynamicReloggerGroup` slouží k vytvoření dynamické skupiny reprotokolovacího nástroje. Členové skupiny reprotokolovacích nástrojů obdrží události jeden od zleva doprava, dokud nebudou zpracovány všechny události v trasování.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parametry

\ *přeprotokolovacích* nástrojů
Vektor ukazatelů [IRelogger](../other-types/irelogger-class.md) obsažených ve skupině dynamického přeprotokolovacího nástroje. Tyto ukazatele můžou být nezpracované, `std::unique_ptr`nebo `std::shared_ptr`. Ukazatele [IAnalyzer](../other-types/ianalyzer-class.md) se také považují za `IRelogger` ukazatelé z důvodu vztahu dědičnosti.

### <a name="return-value"></a>Návratová hodnota

Skupina dynamického přeprotokolovacího nástroje. K zachycení návratové hodnoty použijte klíčové slovo **auto** .

## <a name="remarks"></a>Poznámky

Na rozdíl od skupin statických přeprotokolovacích nástrojů není nutné, aby členové dynamické skupiny přeprotokolovacích souborů byly známy v době kompilace. Můžete zvolit přeprotokolovací členy skupiny za běhu na základě vstupu programu nebo na základě jiných hodnot, které jsou v době kompilace neznámé. Na rozdíl od skupin statických protokolovacích nástrojů mají ukazatele [IRelogger](../other-types/irelogger-class.md) v rámci skupiny dynamického přeprotokolovacího nástroje polymorfní chování a volání virtuální funkce jsou odesílána správně. Tato flexibilita se dodává na náklady na potenciálně pomalejší dobu zpracování událostí. Když jsou všechny členy skupiny reprotokolovacích nástrojů známy v době kompilace a pokud nepotřebujete polymorfní chování, zvažte použití skupiny statických přeprotokolovacích souborů. Chcete-li použít statickou skupinu přeprotokolovacích souborů, zavolejte místo toho [MakeStaticReloggerGroup](make-static-relogger-group.md) .

Skupina dynamického přeprotokolovacího nástroje se dá zapouzdřit do statické skupiny přeprotokolovacích souborů. Adresu předáte do [MakeStaticReloggerGroup](make-static-relogger-group.md). Tuto techniku použijte pro předávání dynamických skupin přeprotokolovacích funkcí, jako je například [relog](relog.md), které akceptují pouze statické skupiny reprotokolovacích nástrojů.

::: moniker-end
