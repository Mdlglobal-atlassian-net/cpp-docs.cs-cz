---
title: Začínáme s C++ Build Insights
description: Přehled sestavení na vysoké úrovni pro C++ .
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325718"
---
# <a name="get-started-with-c-build-insights"></a>Začínáme s C++ Build Insights

::: moniker range="<=vs-2017"

Nástroje Přehledy sestavení C++ jsou dostupné ve Visual Studiu 2019. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights je kolekce nástrojů, které poskytuje lepší přehled o řetězci nástrojů Microsoft Visual C++ (MSVC). Nástroje shromažďují data o sestaveních c++ a prezentují je ve formátu, který vám pomůže odpovědět na běžné otázky, například:

- Jsou moje sestavy dostatečně paralelizované?
- Co mám zahrnout do předkompilované hlavičky (PCH)?
- Existuje konkrétní překážka, na které bych se měl zaměřit, abych zvýšil rychlost sestavení?

Hlavními složkami této technologie jsou:

- *vcperf.exe*, nástroj příkazového řádku, který můžete použít ke shromažďování tras pro vaše sestavení,
- rozšíření Nástroje pro analýzu výkonu systému Windows (WPA), které umožňuje zobrazit trasování sestavení v síti WPA, a
- C++ Build Insights SDK, sada pro vývoj softwaru pro vytváření vlastních nástrojů, které spotřebovávají data C++ Build Insights.

Klikněte na níže uvedené odkazy a rychle začít s těmito komponentami:

[Kurz: vcperf a Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Zjistěte, jak shromažďovat trasování sestavení pro vaše projekty jazyka C++ a jak je zobrazit v WPA.

[Výuka: Základy výkonu systému Windows](tutorials/wpa-basics.md)\
Objevte užitečné tipy WPA pro analýzu trasování sestavení.

[C++ Přehledy sestavení SDK](reference/sdk/overview.md)\
Přehled sady C++ Build Insights SDK.

::: moniker-end
