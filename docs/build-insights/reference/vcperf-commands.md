---
title: 'Reference: příkazy vcperf'
description: Reference k nástroji příkazového řádku vcperf. exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332220"
---
# <a name="reference-vcperf-commands"></a>Reference: příkazy vcperf

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Tento článek obsahuje seznam a popisuje příkazy, které jsou k dispozici v *vcperf. exe*, a jejich použití.

## <a name="commands-to-start-and-stop-traces"></a>Příkazy pro spuštění a zastavení trasování

*Důležité: všechny následující příkazy vyžadují oprávnění správce.*

| Možnost           | Argumenty a popis |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Instruuje *vcperf. exe* za účelem spuštění trasování pod daným názvem relace. V daném počítači může být vždy pouze jedna aktivní relace. <br/><br/> Pokud je zadána možnost `/nocpusampling`, *vcperf. exe* neshromažďuje ukázky procesoru. Zabraňuje použití zobrazení využití procesoru (vzorkování) v analyzátoru výkonu systému Windows, ale shromážděné trasování je menší. <br/><br/> Po spuštění trasování *vcperf. exe* okamžitě vrátí. U všech procesů spuštěných v počítači jsou shromažďovány události v celém systému. To znamená, že nemusíte sestavovat projekt ze stejného příkazového řádku jako ten, který jste použili ke spuštění *vcperf. exe*. Můžete například sestavit projekt ze sady Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Zastaví trasování identifikované daným názvem relace. Spustí krok následného zpracování na trase, aby vygeneroval soubor zobrazitelný v nástroji Windows Performance Analyzer (WPA). Pro nejlepší možnosti zobrazení použijte verzi WPA, která zahrnuje doplněk C++ Build Insights. Další informace najdete v tématu [Začínáme se C++ sestavami Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Parametr `<outputFile.etl>` určuje, kam se má uložit výstupní soubor. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Zastaví trasování identifikované daným názvem relace a zapíše nezpracovaná nezpracovaná data do zadaného výstupního souboru. Výsledný soubor není určen k zobrazení v WPA. <br/><br/> Krok následného zpracování, který je součástí příkazu `/stop`, může někdy mít délku. Tento krok následného zpracování můžete odložit pomocí příkazu `/stopnoanalyze`. Pokud jste připraveni vytvořit soubor zobrazitelný v analyzátoru výkonu Windows, použijte příkaz `/analyze`. |

## <a name="miscellaneous-commands"></a>Další příkazy

| Možnost     | Argumenty a popis |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Přijme nezpracovaný trasovací soubor vytvořený příkazem `/stopnoanalyze`. Spustí krok následného zpracování tohoto trasování a vygeneruje soubor zobrazitelný v nástroji Windows Performance Analyzer. Pro nejlepší možnosti zobrazení použijte verzi WPA, která zahrnuje doplněk C++ Build Insights. Další informace najdete v tématu [Začínáme se C++ sestavami Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Viz také

[Začínáme se C++ sestavami Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Kurz: Základy Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Referenční dokumentace: zobrazení analyzátoru výkonu systému Windows](wpa-views.md)\
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
