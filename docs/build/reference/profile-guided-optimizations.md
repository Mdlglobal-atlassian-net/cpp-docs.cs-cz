---
title: Profilově řízené optimalizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4914b809e8e88ca07cf97af2f4d5405087cf549
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417407"
---
# <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

Optimalizace na základě profilu umožňuje optimalizovat výstupní soubor, kde optimalizátor používá data testovacích běhů souboru .exe nebo .dll. Data představují pravděpodobný výkon programu v provozním prostředí.

Optimalizace na základě profilu jsou dostupné pouze pro nativní cíle x86 nebo x64. Optimalizace na základě profilu nejsou dostupné pro výstupní soubory, které běží na modulu common language runtime. I v případě, že vytvoříte sestavení s smíšená nativní a spravované kódové (s použitím **/CLR** – možnost kompilátoru), nelze použít na základě profilu – optimalizace na pouze pro nativní kód. Pokud se pokusíte sestavit projekt s těmito možnostmi nastavenými v prostředí IDE, výsledky chybu sestavení.

> [!NOTE]
> Informace shromážděné z testovacích běhů profilování potlačení optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](../../build/reference/ob-inline-function-expansion.md) a [/OS, /Ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroky k optimalizaci vaší aplikace

Použití profilováním řízená optimalizace, použijte následující postup optimalizovat aplikaci:

- Kompilaci jednoho nebo více souborů zdrojového kódu s [/GL](../../build/reference/gl-whole-program-optimization.md).

   Všechny moduly sestavené s **/GL** během testovacích běhů optimalizace na základě profilu k zachycení chování za běhu se dají prozkoumat. Všechny moduly v sestavení optimalizace na základě profilu nemá být zkompilovány s **/GL**. Nicméně pouze ty moduly zkompilovaná **/GL** jsou instrumentovány a později dostupné pro optimalizace na základě profilu.

- Odkaz zadáním [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) a [/genprofile nebo /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Použitím **parametru/LTCG** a **/genprofile** nebo **/FASTGENPROFILE** po spuštění instrumentované aplikace se vytvoří soubor .pgd. Po testovacím běhu jsou do souboru .pgd přidána data a lze jej použít jako vstup pro další krok propojování (vytvoření optimalizované bitové kopie). Při zadávání **/genprofile**, můžete volitelně přidat **PGD =**_filename_ argument a zadejte jiný než výchozí název nebo umístění pro soubor .pgd. Kombinace **parametru/LTCG** a **/genprofile** nebo **/FASTGENPROFILE** možnosti linkeru nahradí zastaralá **/LTCG:PGINSTRUMENT** – možnost linkeru.

- Profilování aplikace.

   Pokaždé, když skončí profilovaná relace EXE nebo profilovaná knihovna DLL je uvolněna, *appname*! # .pgc soubor se vytvoří. Soubor .pgc obsahuje informace o konkrétním testovacím běhu aplikace. # je číslo od 1, které se zvyšuje podle počtu jiných *appname*! # .pgc soubory v adresáři. Nepředstavuje-li testovací běh scénář, který má být optimalizován, lze soubor .pgc odstranit.

   Během testovacího běhu, můžete vynutit uzavření aktuálně otevřeného souboru .pgc a vytvoření nového souboru .pgc pomocí [pgosweep](../../build/reference/pgosweep.md) utility (například když na konec testovací scénář se neshoduje s aplikací).

   Aplikace můžete také přímo vyvolat funkci PGO [PgoAutoSweep](pgoautosweep.md), k zaznamenání dat profilu místě volání jako soubor .pgc. To vám může jemnější kontrolu nad kódem předmětem zachycená data ve vašich souborech .pgc. Příklad toho, jak tuto funkci použít, najdete v článku [PgoAutoSweep](pgoautosweep.md) dokumentaci.

   Při vytváření instrumentované sestavení, ve výchozím nastavení shromažďování dat se provádí v režimu není bezpečné pro vlákna, který je rychlejší, ale nemusí být zcela přesné. S použitím **EXACT** argument **/genprofile** nebo **/FASTGENPROFILE**, shromažďování dat můžete zadat v režimu bezpečné pro vlákna, což je přesnější ale pomalejší. Tato možnost je také k dispozici, pokud jste nastavili zastaralá [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) proměnné prostředí nebo zastaralá **/POGOSAFEMODE** – možnost linkeru, když vytvoříte instrumentované sestavení.

- Odkaz zadáním **parametru/LTCG** a **/useprofile**.

   Použít **parametru/LTCG** a [/useprofile](useprofile.md) možnosti propojovacího programu k vytvoření optimalizované bitové kopie. Vstupem pro tento krok je soubor .pgd. Při zadání **/useprofile**, můžete volitelně přidat **PGD =**_filename_ argumentu pro zadání jiné než výchozí název nebo umístění pro soubor .pgd. Tento název můžete zadat také pomocí zastaralá **/PGD** – možnost linkeru. Kombinace **parametru/LTCG** a **/useprofile** nahradí zastaralá **/LTCG:PGOPTIMIZE** a **/LTCG:PGUPDATE** možnosti linkeru.

Lze dokonce vytvořit optimalizovaný výstupní soubor a později určit, že pro vytvoření více optimalizované bitové kopie by bylo užitečné další profilování. Pokud instrumentovaná bitová kopie a její soubor .pgd k dispozici, můžete provést dodatečné testovací běhy a optimalizovanou bitovou kopii znovu s novým souborem .pgd, pomocí stejného **parametru/LTCG** a **/useprofile** možnosti linkeru .

## <a name="optimizations-performed-by-pgo"></a>Optimalizace prováděné PGO

Následuje seznam optimalizací na základě profilu:

- **Vkládání** – například, pokud existuje funkce A že často volá funkci B a je funkce B relativně malá, pak se optimalizace na základě profilu vloží funkci B do funkce A.

- **Spekulace o virtuálních voláních** – Pokud virtuální volání nebo jiné volání pomocí ukazatele na funkci často cílí na určitou funkci, optimalizace profilu může vložit podmíněně spouštěné přímé volání do často cílené funkce a přímé volání může být vložená.

- **Přidělení registru** – optimalizace pomocí dat profilu za následek lepší přidělování registru.

- **Optimalizace základních bloků** – optimalizace základních bloků umožňuje běžně spouštěných základních bloků, které dočasně spouštěny uvnitř daného rámce, do stejné sady stránek (umístění). Tím je minimalizován počet použitých stránek, a tedy i zatížení paměti.

- **Optimalizace velikosti/rychlosti** – funkce, kde program stráví mnoho času, lze optimalizovat rychlost.

- **Rozložení funkcí** – na základě grafu volání a Profilovat chování volajícího/volaného jsou funkce, které bývají na stejné cestě spouštění umístěné ve stejné části.

- **Podmíněná optimalizace větví** – pomocí sond hodnot na základě profilu – optimalizace najdete, pokud je daná hodnota v příkazu switch používána častěji než jiné hodnoty.  Tuto hodnotu lze pak z příkazu switch odstranit.  Totéž lze provést s instrukcemi if/else, kde optimalizátor může příkaz if/else uspořádat tak, že je jako první umístěn blok if nebo else v závislosti na tom, který z nich je častěji vyhodnocen na hodnotu true.

- **Oddělení mrtvého kódu** -kód, který během profilování nebyl zavolán se přesune do zvláštního oddílu, která se připojuje ke konci sady oddílů. Tím je tento oddíl efektivně udržován mimo často používané stránky.

- **Oddělení kódu EH** – kód The EH, probíhá jen výjimečně, lze často přesunout do odděleného oddílu při optimalizace na základě profilu mohou určit, že k výjimkám dochází jen za výjimečných podmínek.

- **Vnitřní objekty paměti** – o rozšíření vnitřních objektů můžete lépe rozhodnout, pokud jej lze určit, zda jsou volány často. Vnitřní objekt lze optimalizovat také na základě velikosti bloku operací přesunutí nebo kopírování.

Pokud používáte Visual Studio 2013, můžete použít automatizované [modulu Plug-In optimalizace na základě profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) pro jazyk Visual C++ v Centru pro výkon a Diagnostika jim zjednoduší a zefektivní proces optimalizace v sadě Visual Studio. Tento modul plug-in není k dispozici v pozdějších verzích sady Visual Studio.

## <a name="next-steps"></a>Další kroky

Další informace o těchto proměnných prostředí, funkce a nástroje, které můžete použít v optimalizace na základě profilu:

[Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Tyto proměnné lze použít k určení chování za běhu testování scénářů. Jsou zastaralé a místo toho použití nové možnosti linkeru; Tady můžete přesunout z proměnných prostředí, možnosti linkeru.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkce můžete přidat do své aplikace a poskytují podrobné .pgc ovládacího prvku zachycení dat souborů.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Nástroj příkazového řádku, který zapíše všechna data profilu k souboru .pgc zavře soubor .pgc a otevře se nový soubor .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Nástroj příkazového řádku, který přidá data profilu z jednoho nebo více souborů .pgc soubor .pgd.

[Postupy: Sloučení několika profilů PGO do jediného profilu](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Příklady **pgomgr** využití.

## <a name="see-also"></a>Viz také:

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)
