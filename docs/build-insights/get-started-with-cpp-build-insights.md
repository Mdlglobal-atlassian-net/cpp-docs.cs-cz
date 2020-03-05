---
title: Začínáme s C++ Build Insights
description: Podrobný přehled C++ buildu Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332004"
---
# <a name="get-started-with-c-build-insights"></a>Začínáme s C++ Build Insights

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Přehledy buildu jsou kolekce nástrojů, které poskytují lepší přehled o řetězcích C++ nástrojů Microsoft Visual (MSVC). Nástroje shromažďují data o vašich C++ sestaveních a prezentují je ve formátu, který vám může přispět k zodpovězení běžných otázek, třeba:

- Jsou moje buildy dostatečně paralelismuované?
- Co mám zahrnout do předkompilované hlavičky (PCH)?
- Je k dispozici konkrétní kritická místa, která by se měla soustředit na zvýšení rychlosti sestavení?

Hlavními komponentami této technologie jsou:

- *vcperf. exe*, nástroj příkazového řádku, který můžete použít ke shromáždění trasování pro sestavení,
- rozšíření Windows Performance Analyzer (WPA), které umožňuje zobrazit trasování sestavení v WPA a
- Sada C++ SDK pro Build Insights, sada Software Development Kit pro vytváření vlastních nástrojů využívajících C++ data Build Insights.

Pokud chcete rychle začít s těmito součástmi, klikněte na odkazy níže:

[Kurz: vcperf and Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Naučte se shromažďovat trasování sestavení pro vaše C++ projekty a jak je zobrazit v WPA.

[Kurz: Základy výkonu Windows](tutorials/wpa-basics.md)\
Seznamte se s užitečnými tipy WPA pro analýzu trasování sestavení.

\ Build Insights SDK [ C++ ](reference/sdk/overview.md)
Přehled sady SDK pro C++ Build Insights

::: moniker-end
