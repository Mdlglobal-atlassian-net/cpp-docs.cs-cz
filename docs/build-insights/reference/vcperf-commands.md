---
title: 'Reference: příkazy vcperf'
description: Reference pro nástroj příkazového řádku vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323242"
---
# <a name="reference-vcperf-commands"></a>Reference: příkazy vcperf

::: moniker range="<=vs-2017"

Nástroje Přehledy sestavení C++ jsou dostupné ve Visual Studiu 2019. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

Tento článek uvádí a popisuje příkazy, které jsou k dispozici v *vcperf.exe*a jak je používat.

## <a name="commands-to-start-and-stop-traces"></a>Příkazy pro spuštění a zastavení trasování

*DŮLEŽITÉ: Všechny následující příkazy vyžadují oprávnění správce.*

| Možnost           | Argumenty a popis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | *Sděluje vcperf.exe* spustit trasování pod danýnázev relace. V daném počítači může být současně pouze jedna aktivní relace. <br/><br/> Pokud `/nocpusampling` je tato možnost zadána, *vcperf.exe* neshromažďuje vzorky procesoru. Zabraňuje použití zobrazení využití procesoru (sampled) v nástroji Windows Performance Analyzer, ale zmenší shromážděné trasování. <br/><br/> Po spuštění trasování *se vcperf.exe* okamžitě vrátí. Události jsou shromažďovány v celém systému pro všechny procesy spuštěné v počítači. To znamená, že projekt není nutné vytvářet ze stejného příkazového řádku jako ten, který jste použili ke spuštění *vcperf.exe*. Například můžete vytvořit projekt z Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Zastaví trasování identifikované daným názvem relace. Spustí krok po zpracování na trasování generovat soubor zobrazitelný v nástroji Windows Performance Analyzer (WPA). Pro nejlepší zobrazení použijte verzi WPA, která obsahuje doplněk C++ Build Insights. Další informace najdete [v tématu Začínáme s C++ Přehledy sestavení](/cpp/build-insights/get-started-with-cpp-build-insights). Parametr `<outputFile.etl>` určuje, kam má být uložen výstupní soubor. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Zastaví trasování identifikované daným názvem relace a zapíše nezpracovaná nezpracovaná data do zadaného výstupního souboru. Výsledný soubor není určen k zobrazení v WPA. <br/><br/> Krok následného zpracování zapojený `/stop` do příkazu může být někdy zdlouhavý. `/stopnoanalyze` Příkaz můžete použít ke zpoždění tohoto kroku následného zpracování. `/analyze` Tento příkaz použijte, když jste připraveni vytvořit soubor zobrazitelný v nástroji Windows Performance Analyzer. |

## <a name="miscellaneous-commands"></a>Různé příkazy

| Možnost     | Argumenty a popis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Přijme nezpracovaný trasovací soubor `/stopnoanalyze` vytvořený příkazem. Spustí krok po zpracování na toto trasování generovat soubor zobrazitelný v nástroji Windows Performance Analyzer. Pro nejlepší zobrazení použijte verzi WPA, která obsahuje doplněk C++ Build Insights. Další informace najdete [v tématu Začínáme s C++ Přehledy sestavení](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Viz také

[Začínáme s Přehledy sestavení c++](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Kurz: Základy nástroje Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Reference: Zobrazení nástroje Windows Performance Analyzer](wpa-views.md)\
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
