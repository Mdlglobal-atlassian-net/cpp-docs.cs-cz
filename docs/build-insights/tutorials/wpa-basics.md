---
title: 'Kurz: Základy nástroje Windows Performance Analyzer'
description: Návod, jak dokončit základní operace v nástroji Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323406"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Kurz: Základy nástroje Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje Přehledy sestavení C++ jsou dostupné ve Visual Studiu 2019. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

Efektivní používání přehledů sestavení jazyka C++ vyžaduje určité znalosti nástroje Windows Performance Analyzer (WPA). Tento článek vám pomůže seznámit se s běžnými operacemi WPA. Další informace o použití nástroje WPA naleznete v dokumentaci [k nástroji Windows Performance Analyzer.](/windows-hardware/test/wpt/windows-performance-analyzer)

## <a name="change-the-view-mode"></a>Změna režimu zobrazení

WPA nabízí dva základní režimy zobrazení, abyste mohli prozkoumat vaše stopy:

- režimu grafu a
- v režimu tabulky.

Mezi nimi můžete přepínat pomocí ikon režimu zobrazení v horní části podokna zobrazení:

![Přepínání mezi režimem grafu a režimem tabulky.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Vybrat přednastavení

Většina zobrazení WPA přehledů sestavení c++ má více přednastavení, ze kterých si můžete vybrat. Požadované přednastavení můžete vybrat pomocí rozevírací nabídky v horní části podokna zobrazení:

![Výběr přednastavení.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Přiblížení a oddálení

Některé stopy sestavení jsou tak velké, že je těžké rozeznat detaily. Chcete-li přiblížit oblast, která vás zajímá, klikněte pravým tlačítkem myši na graf a vyberte možnost **Lupa**. Vždy se můžete vrátit k předchozímu nastavení tak, že zvolíte **Zpět zoom**. Tento obrázek znázorňuje příklad použití výběru a příkazu **Lupa** pro přiblížení části grafu:

![Přiblížení grafu.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Seskupit podle různých sloupců

Způsob zobrazení trasování můžete přizpůsobit. Klikněte na ikonu ozubeného kola v horní části podokna zobrazení a změňte uspořádání sloupců v Editoru zobrazení Průzkumníka sestavení. Sloupce, které se nacházejí nad žlutou čárou v tomto dialogovém okně, jsou ty, podle kterých jsou řádky dat seskupeny. Sloupec přímo nad žlutou čárou je zvláštní: v zobrazení grafu je zobrazen na barevných pruhech.

Tento obrázek znázorňuje ukázkový pruhový graf vyvolání odkazu. K otevření dialogového okna Editor zobrazení průzkumníka sestavení se používá ikona ozubeného kola. Potom přetáhneme položky sloupce Komponenta a Název nad žlutou čáru. Konfigurace se změní zvýšit úroveň podrobností a zjistit, co se skutečně stalo uvnitř propojovacího programu:

![Přiblížení grafu.](media/wpa-grouping.gif)

## <a name="see-also"></a>Viz také

[Kurz: vcperf a Windows Performance Analyzer](vcperf-and-wpa.md)\
[Reference: příkazy vcperf](/cpp/build-insights/reference/vcperf-commands)\
[Reference: Zobrazení nástroje Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
