---
title: 'C++Přehledy sestavení: Základy Windows Performance Analyzer'
description: Kurz k dokončení základních operací v nástroji Windows Performance Analyzer
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4bd91698561175d876b7a3351a0ed6e85ef73a35
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633082"
---
# <a name="c-build-insights-windows-performance-analyzer-basics"></a>C++Přehledy sestavení: Základy Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Používání C++ přehledů sestavení efektivně vyžaduje znalost Windows Performance Analyzer (WPA). Tento článek vám pomůže se seznámení s běžnými operacemi WPA. Další informace o tom, jak používat protokol WPA, najdete v dokumentaci ke službě [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) .

## <a name="change-the-view-mode"></a>Změna režimu zobrazení

WPA nabízí dva základní režimy zobrazení, abyste mohli prozkoumat trasování:

- režim grafu a
- režim tabulky

Mezi nimi můžete přepínat pomocí ikon režimu zobrazení v horní části podokna zobrazení:

![Přepínání mezi režimem grafu a režimem tabulky.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Vybrat předvolby

Většina C++ zobrazení pro přehledy v protokolech WPA obsahuje několik přednastavení, ze kterých si můžete vybrat. Požadovanou předvolbu můžete vybrat pomocí rozevírací nabídky v horní části podokna zobrazení:

![Výběr přednastavení.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Přiblížení a oddálení

Některá trasování sestavení jsou tak velká, takže je obtížné udělat si podrobnosti. Pokud se chcete přiblížit k oblasti, která vás zajímá, klikněte pravým tlačítkem myši na graf a vyberte možnost **Zvětšit**. Na předchozí nastavení se můžete kdykoli vrátit kliknutím na **zrušit přiblížení**. Tento obrázek ukazuje příklad použití výběru a příkazu **lupy** k přiblížení v části grafu:

![Přiblížení v grafu.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Seskupit podle různých sloupců

Můžete přizpůsobit způsob zobrazení trasování. Klikněte na ikonu ozubeného kolečka v horní části podokna zobrazení a znovu uspořádejte sloupce v editoru zobrazení Průzkumníka sestavení. Sloupce nacházející se nad žlutou čárou v tomto dialogovém okně jsou ty, podle kterých jsou datové řádky seskupeny. Sloupec vpravo nad žlutou čárou je speciální: v zobrazení grafu se zobrazí na barevných pruzích.

Tento obrázek ukazuje vzorový pruhový graf volání propojení. Pomocí ikony ozubeného kolečka se otevře dialogové okno Editor zobrazení Průzkumníka sestavení. Pak přetáhneme položky sloupce Component a Name nad žlutou čáru. Konfigurace se změní, aby se zvýšila úroveň podrobností, a viděli, co skutečně bylo uvnitř linkeru:

![Přiblížení v grafu.](media/wpa-grouping.gif)

## <a name="see-also"></a>Viz také:

[Začínáme se C++ sestavami Build Insights](get-started-with-cpp-build-insights.md)\
[referenční\ vcperf. exe](vcperf-reference.md)
[Referenční\ zobrazení analyzátoru výkonu systému Windows](wpa-views-reference.md)
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
