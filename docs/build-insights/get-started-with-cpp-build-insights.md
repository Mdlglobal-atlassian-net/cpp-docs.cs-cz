---
title: Začínáme s C++ Build Insights
description: Podrobný přehled C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759222"
---
# <a name="get-started-with-c-build-insights"></a>Začínáme s C++ Build Insights

::: moniker range="<=vs-2017"

Nástroje C++ Build Insights jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor **verzí** sady Visual Studio pro tento článek na sadu visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights je kolekce nástrojů, které poskytují lepší přehled o řetězcích nástrojů Microsoft Visual C++ (MSVC). Nástroje shromažďují data o sestaveních C++ a prezentují je ve formátu, který vám může přispět k zodpovězení běžných otázek, třeba:

- Jsou moje buildy dostatečně paralelismuované?
- Co mám zahrnout do předkompilované hlavičky (PCH)?
- Je k dispozici konkrétní kritická místa, která by se měla soustředit na zvýšení rychlosti sestavení?

Hlavními komponentami této technologie jsou:

- *vcperf. exe*, nástroj příkazového řádku, který můžete použít ke shromáždění trasování pro sestavení,
- rozšíření Windows Performance Analyzer (WPA), které umožňuje zobrazit trasování sestavení v WPA a
- C++ Build Insights SDK, sada Software Development Kit pro vytváření vlastních nástrojů, které využívají data C++ Build Insights.

## <a name="documentation-sections"></a>Oddíly dokumentace

[Kurz: vcperf and Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Naučte se shromažďovat trasování sestavení pro projekty C++ a jak je zobrazit v WPA.

[Kurz: Základy výkonu systému Windows](tutorials/wpa-basics.md)\
Seznamte se s užitečnými tipy WPA pro analýzu trasování sestavení.

[Sada SDK pro C++ Build Insights](reference/sdk/overview.md)\
Přehled sady C++ Build Insights SDK.

## <a name="articles"></a>Články

Přečtěte si tyto články z oficiálního blogu týmu v jazyce C++, kde najdete další informace o přehledech sestavení C++:

[Představujeme C++ Build Insights](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[Analyzovat sestavení programově pomocí sady C++ Build Insights SDK](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[Hledání slabých míst sestavení pomocí C++ Build Insights](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[Rychlejší buildy pomocí návrhů PCH z C++ Build Insights](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end
