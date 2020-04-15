---
title: 'Reference: Zobrazení nástroje Windows Performance Analyzer'
description: Odkaz na zobrazení přehledů sestavení c++ dostupných v nástroji Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b54b1b76d83b77ec7b8d8d3309d81ed9eb2db2d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323239"
---
# <a name="reference-windows-performance-analyzer-views"></a>Reference: Zobrazení nástroje Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje Přehledy sestavení C++ jsou dostupné ve Visual Studiu 2019. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

Tento článek obsahuje podrobnosti o každém zobrazení sestavení c++ sestavení k dispozici v nástroji Windows Performance Analyzer (WPA). Na této stránce můžete najít:

- popisy datových sloupců; A
- přednastavení pro každé zobrazení, včetně jejich zamýšleného použití a preferovaného režimu zobrazení.

Pokud s WPA teprve začínáte, doporučujeme, abyste se nejprve seznámili se [základy WPA pro C++ Přehledy sestavení](/cpp/build-insights/tutorials/wpa-basics).

## <a name="build-explorer"></a>Průzkumník sestavení

Zobrazení Průzkumník sestavení se používá k:

- diagnostikovat problémy s paralelismem,
- určit, zda čas sestavení dominuje analýza, generování kódu nebo propojení a
- identifikovat úzká místa a neobvykle dlouhé činnosti sestavení.

### <a name="build-explorer-view-data-columns"></a>Sloupce dat zobrazení zobrazení Aplikace Build Explorer

| Název sloupce | Popis |
|-|-|
| BuildTimelineDescription | Textový popis časové osy, na které dochází k aktuální aktivitě nebo vlastnosti. |
| BuildTimelineId          | Identifikátor založený na nule pro časovou osu, na které dochází k aktuální aktivitě nebo vlastnosti. |
| Komponenta                | Součást, která je kompilována nebo propojena při vyzařování aktuální události. Hodnota tohoto sloupce * \<je Vyvolání\> X Info,* pokud žádná součást je přidružena k této události. X je jedinečný číselný identifikátor pro vyvolání, které bylo spuštěno v době, kdy byla událost emitována. Tento identifikátor je stejný jako identifikátor ve sloupci InvocationId pro tuto událost. |
| Počet                    | Počet aktivit nebo vlastností reprezentované tímto datovým řádkem. Tato hodnota je vždy 1 a je užitečné pouze ve scénářích agregace při seskupování více řádků. |
| ExclusiveCPUTime         | Množství času procesoru v milisekundách používaných touto aktivitou. Čas strávený v podřízených aktivitách není zahrnut v této částce. |
| ExclusiveDuration        | Milisekunda trvání aktivity. Doba trvání podřízených aktivit není zahrnuta v této částce. |
| Inkluzivní procesorový čas         | Množství času procesoru v milisekundách používaných touto aktivitou a všechny podřízené aktivity. |
| Inkluzívní doba trvání        | Milisekunda trvání této aktivity, včetně všech podřízených aktivit. |
| VyvoláníPopis    | Textový popis vyvolání této události došlo v. Popis zahrnuje, zda byl *cl.exe* nebo *link.exe*a jedinečný identifikátor číselného vyvolání. Pokud je to možné, obsahuje úplnou cestu k komponentě zkompilované nebo propojené během vyvolání. Pro vyvolání, které nevytvářejí žádnou součást, nebo pro ty, které vytvářejí více součástí, je cesta prázdná. Identifikátor vyvolání je stejný jako ve sloupci InvocationId. |
| VyvoláníIIda             | Jedinečný číselný identifikátor pro vyvolání této události došlo v. |
| Name (Název)                     | Název aktivity nebo vlastnosti reprezentované touto událostí. |
| Time                     | Časové razítko, které identifikuje, kdy k události došlo. |
| Nástroj                     | Nástroj, který se provádí, když k této události došlo. Hodnota tohoto sloupce je CL nebo Odkaz. |
| Typ                     | Typ aktuální události. Tato hodnota je aktivita nebo Vlastnost. |
| Hodnota                    | Pokud je aktuální událost vlastnost, tento sloupec obsahuje jeho hodnotu. Tento sloupec zůstane prázdný, pokud je aktuální událost aktivitou. |

### <a name="build-explorer-view-presets"></a>Přednastavení zobrazení Build Explorer

| Název přednastavení           | Upřednostňovaný režim zobrazení | Jak používat |
|-----------------------|---------------------|------------|
| Statistika aktivity   | Graf / Tabulka       | Toto přednastavení slouží k zobrazení agregovaných statistik pro všechny aktivity Průzkumníka sestavení. V režimu tabulky na první pohled řekněte, jestli sestavení dominuje analýza, generování kódu nebo propojovací program. Agregované doby trvání pro každou aktivitu jsou seřazeny v sestupném pořadí. Přejděte na rozšíření horní uzel snadno zjistit, které vyvolání trvat nejvíce času pro tyto nejvyšší aktivity. Pokud chcete, můžete upravit nastavení WPA tak, aby zobrazovala průměry nebo jiné typy agregací. V režimu grafu, podívejte se, kdy je každá aktivita aktivní během sestavení. |
| Vyvolání           | Graph               | Posuňte se dolů seznamem vyvolání v zobrazení grafu seřazených podle času zahájení. Můžete jej použít společně se zobrazením CPU (Sampled) k vyhledání vyvolání, která jsou zarovnána s nízkými zónami využití procesoru. Detekujte problémy s paralelismem. |
| Vlastnosti vyvolání | Table               | Rychle najít klíčové informace o dané vyvolání kompilátoru nebo propojovacího systému. Určete jeho verzi, pracovní adresář nebo úplný příkazový řádek použitý k jeho vyvolání. |
| Časové osy             | Graph               | Podívejte se na pruhový graf, jak byla vaše sestavení paralelizována. Na první pohled identifikujte problémy s paralelismem a úzká místa. Nakonfigurujte WPA tak, aby přiřazovala barům různé významy podle vašich potřeb. Zvolte popisy vyvolání jako poslední seskupený sloupec, chcete-li zobrazit barevně kódovaný pruhový graf všech vašich vyvolání. Pomáhá vám rychle identifikovat časově náročné viníky. Potom přibližte zobrazení a zvolte název aktivity jako poslední seskupený sloupec, abyste viděli nejdelší části. |

## <a name="files"></a>Soubory

Zobrazení Soubory se používá k:

- určit, které hlavičky jsou zahrnuty nejčastěji, a
- vám pomohou rozhodnout, co zahrnout do předkompilované hlavičky (PCH).

### <a name="files-view-data-columns"></a>Soubory zobrazují datové sloupce

| Název sloupce              | Popis |
|--------------------------|-------------|
| Název_aktivity             | Probíhající aktivita při vyprávění této události souboru. V současné době je tato hodnota vždy *analýza*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponenta                | * |
| Počet                    | * |
| Hloubka                    | Pozice založená na nule ve stromu zahrnutí, ve kterém je tento soubor nalezen. Počítání začíná v kořenovém adresáři stromu zahrnutí. Hodnota 0 obvykle odpovídá souboru .c/.cpp. |
| ExclusiveDuration        | * |
| Includedby               | Úplná cesta k souboru, který obsahoval aktuální soubor. |
| ZahrnutyCesta             | Úplná cesta k aktuálnímu souboru. |
| Inkluzívní doba trvání        | * |
| VyvoláníIIda             | * |
| StartTime                | Časové razítko, které představuje čas, kdy byla vyzařována aktuální událost souboru. |
| Nástroj                     | * |

\*Hodnota tohoto sloupce je stejná jako v zobrazení [Průzkumníka sestavení.](#build-explorer-view-data-columns)

### <a name="files-view-presets"></a>Přednastavení zobrazení souborů

| Název přednastavení | Upřednostňovaný režim zobrazení | Jak používat |
|-------------|---------------------|------------|
| Statistika  | Table               | Podívejte se na seznam v sestupném pořadí, které soubory měly nejvyšší agregovaný čas analýzy. Tyto informace vám pomohou restrukturalizovat záhlaví nebo se rozhodnout, co zahrnout do pch. |

## <a name="functions"></a>Functions

Zobrazení Funkce se používá k identifikaci funkcí s příliš dlouhou dobu generování kódu.

### <a name="functions-view-data-columns"></a>Funkce zobrazení datových sloupců

| Název sloupce              | Popis |
|--------------------------|-------------|
| Název_aktivity             | Probíhající aktivita při vyprávění této události funkce. V současné době tato hodnota je vždy *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Komponenta                | * |
| Počet                    | * |
| Doba trvání                 | Doba trvání aktivity generování kódu pro tuto funkci. |
| Název funkce             | Název funkce, která prochází generováním kódu. |
| VyvoláníIIda             | * |
| StartTime                | Časové razítko, které představuje, když byla vyzařována aktuální událost funkce. |
| Nástroj                     | * |

\*Hodnota tohoto sloupce je stejná jako v zobrazení [Průzkumníka sestavení.](#build-explorer-view-data-columns)

### <a name="functions-view-presets"></a>Přednastavení zobrazení funkcí

| Název přednastavení | Upřednostňovaný režim zobrazení | Jak používat |
|-------------|---------------------|------------|
| Statistika  | Table               | Podívejte se na seznam v sestupném pořadí, které funkce měly nejvyšší čas generování agregovaného kódu. Mohou naznačovat, kde váš kód nadhodní klíčové slovo **__forceinline** nebo že některé funkce mohou být příliš velké. |
| Časové osy   | Graph               | Podívejte se na tento sloupcový graf, abyste se dozvěděli umístění a dobu trvání funkcí, které se generují nejvíce. Podívejte se, jestli jsou zarovnány s kritickými místy v zobrazení Průzkumník sestavení. Pokud ano, proveďte příslušná opatření ke zkrácení doby generování kódu a prospěch u vašich časů sestavení. |

## <a name="see-also"></a>Viz také

[Začínáme s Přehledy sestavení c++](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Reference: příkazy vcperf](vcperf-commands.md)\
[Kurz: Základy nástroje Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
