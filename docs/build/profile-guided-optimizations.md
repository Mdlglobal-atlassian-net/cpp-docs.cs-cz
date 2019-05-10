---
title: Optimalizace na základě profilu
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857329"
---
# <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

Profilově řízené optimalizace (PGO) umožňuje optimalizovat zcela spustitelného souboru, kde Optimalizátor používá data testovacích běhů souboru .exe nebo .dll. Data představují pravděpodobně výkon programu v produkčním prostředí.

Optimalizace na základě profilu jsou dostupné pouze pro nativní cíle x86 nebo x64. Optimalizace na základě profilu nejsou k dispozici pro spustitelné soubory, které běží na modulu common language runtime. I v případě, že vytvoříte sestavení s smíšená nativní a spravované kódové (s použitím **/CLR** – možnost kompilátoru), nelze použít na základě profilu – optimalizace na pouze pro nativní kód. Pokud se pokusíte sestavit projekt s těmito možnostmi nastavenými v prostředí IDE, výsledky chybu sestavení.

> [!NOTE]
> Informace shromážděné z testovacích běhů profilování potlačení optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](reference/ob-inline-function-expansion.md) a [/OS, /Ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroky k optimalizaci vaší aplikace

Použití profilováním řízená optimalizace, použijte následující postup optimalizovat aplikaci:

- Kompilaci jednoho nebo více souborů zdrojového kódu s [/GL](reference/gl-whole-program-optimization.md).

   Všechny moduly sestavené s **/GL** během testovacích běhů optimalizace na základě profilu k zachycení chování za běhu se dají prozkoumat. Všechny moduly v sestavení optimalizace na základě profilu nemá být zkompilovány s **/GL**. Nicméně pouze ty moduly zkompilovaná **/GL** jsou instrumentovány a později dostupné pro optimalizace na základě profilu.

- Odkaz zadáním [parametru/LTCG](reference/ltcg-link-time-code-generation.md) a [/genprofile nebo /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Použitím **parametru/LTCG** a **/genprofile** nebo **/FASTGENPROFILE** vytvoří `.pgd` souboru při spuštění instrumentované aplikace. Po testovacím běhu data je přidána do `.pgd` souboru, může sloužit jako vstup pro další krok propojování (Vytvoření optimalizované bitové kopie). Při zadávání **/genprofile**, můžete volitelně přidat **PGD =**_filename_ argument a zadejte jiný než výchozí název nebo umístění pro `.pgd` souboru. Kombinace **parametru/LTCG** a **/genprofile** nebo **/FASTGENPROFILE** možnosti linkeru nahradí zastaralá **/LTCG:PGINSTRUMENT** – možnost linkeru.

- Profilování aplikace.

   Pokaždé, když skončí profilovaná relace EXE nebo profilovaná knihovna DLL je uvolněna, `appname!N.pgc` se vytvoří soubor. A `.pgc` soubor obsahuje informace o testovacím běhu konkrétní aplikace. *AppName* je název vaší aplikace a *N* je číslo od 1, které se zvyšuje podle počtu jiných `appname!N.pgc` soubory v adresáři. Můžete odstranit `.pgc` souboru, pokud testovací běh nepředstavuje scénáři chcete optimalizovat.

   Během testovacího běhu lze vynutit uzavření aktuálně otevřeného `.pgc` souboru a vytvoření nového `.pgc` souboru [pgosweep](pgosweep.md) utility (například když na konec testovací scénář nemá shodovat se aplikace vypnutí).

   Aplikace můžete také přímo vyvolat funkci PGO [PgoAutoSweep](pgoautosweep.md), k zaznamenání dat profilu místě volání jako `.pgc` souboru. Poskytuje lepší kontrolu nad kódem předmětem zachycená data ve vašich `.pgc` soubory. Příklad toho, jak tuto funkci použít, najdete v článku [PgoAutoSweep](pgoautosweep.md) dokumentaci.

   Při vytváření instrumentované sestavení, ve výchozím nastavení shromažďování dat se provádí v režimu není bezpečné pro vlákna, který je rychlejší, ale mohou být nepřesná. S použitím **EXACT** argument **/genprofile** nebo **/FASTGENPROFILE**, shromažďování dat můžete zadat v režimu bezpečné pro vlákna, což je přesnější, ale pomalejší. Tato možnost je také k dispozici, pokud jste nastavili zastaralá [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) proměnné prostředí nebo zastaralá **/POGOSAFEMODE** – možnost linkeru, když vytvoříte instrumentované sestavení.

- Odkaz zadáním **parametru/LTCG** a **/useprofile**.

   Použít **parametru/LTCG** a [/useprofile](reference/useprofile.md) možnosti propojovacího programu k vytvoření optimalizované bitové kopie. Tento krok přijímá jako vstupní `.pgd` souboru. Při zadání **/useprofile**, Volitelně můžete přidat **PGD =**_filename_ argumentu pro zadání jiné než výchozí název nebo umístění `.pgd` souboru. Tento název můžete zadat také pomocí zastaralá **/PGD** – možnost linkeru. Kombinace **parametru/LTCG** a **/useprofile** nahradí zastaralá **/LTCG:PGOPTIMIZE** a **/LTCG:PGUPDATE** možnosti linkeru.

Je dokonce možné k vytvoření optimalizované spustitelný soubor a později určit, že další profilace budou užitečné k vytvoření více optimalizované bitové kopie. -Li instrumentovaná bitová kopie a její `.pgd` souboru jsou k dispozici, můžete provést dodatečné testovací běhy a optimalizovanou bitovou kopii s novější znovu sestavit `.pgd` soubor pomocí stejné **parametru/LTCG** a   **/useprofile** možnosti linkeru.

## <a name="optimizations-performed-by-pgo"></a>Optimalizace prováděné PGO

Optimalizace na základě profilu zahrnují tyto kontroly a vylepšení:

- **Vkládání** – například, pokud funkce A často volá funkci B a funkce B je poměrně málo početnému a potom na základě profilu – optimalizace vloží funkci B do funkce A.

- **Spekulace o virtuálních voláních** – Pokud virtuální volání nebo jiné volání pomocí ukazatele na funkci často cílí na určitou funkci, optimalizace profilu může vložit podmíněně prováděnou přímého volání do často cílené funkce, a přímé volání může být vložená.

- **Přidělení registru** – optimalizace založená na profilu data následek lepší přidělování registru.

- **Optimalizace základních bloků** – optimalizace základních bloků umožňuje běžně spouštěných základních bloků, které dočasně spouštěny uvnitř daného rámce, do stejné sady stránek (umístění). Minimalizuje počet použitých stránek, které minimalizuje režijní náklady na paměť.

- **Optimalizace velikosti/rychlosti** – kde program stráví nejvíce času spuštění funkce, lze optimalizovat rychlost.

- **Rozložení funkcí** – na základě grafu volání a Profilovat chování volajícího/volaného jsou funkce, které bývají na stejné cestě spouštění umístěné ve stejné části.

- **Podmíněná optimalizace větví** – pomocí sond hodnot na základě profilu – optimalizace najdete, pokud je daná hodnota v příkazu switch používána častěji než jiné hodnoty.  Tuto hodnotu lze pak z příkazu switch odstranit.  Totéž lze provést s `if`... `else` pokyny, kde optimalizátor může příkaz `if`... `else` tak že buď `if` nebo `else` bloku je jako první umístěn, v závislosti na tom, který je častěji hodnotu true.

- **Oddělení mrtvého kódu** -kód, který během profilování nebyl zavolán se přesune do zvláštního oddílu, která se připojuje ke konci sady oddílů. Efektivně udržován mimo často používané stránky v této části.

- **Oddělení kódu EH** – kód EH protože je jen výjimečně, ji lze často přesunout do odděleného oddílu. Je přesunout, pokud optimalizace na základě profilu mohou určit, že k výjimkám dochází jen za výjimečných podmínek.

- **Vnitřní objekty paměti** – ať rozbalit vnitřní objekt, nebo Ne, závisí na tom, zda jsou volány často. Vnitřní objekt lze optimalizovat také na základě velikosti bloku operací přesunutí nebo kopírování.

## <a name="next-steps"></a>Další kroky

Další informace o těchto proměnných prostředí, funkce a nástroje, které můžete použít v optimalizace na základě profilu:

[Proměnné prostředí pro optimalizace na základě profilu](environment-variables-for-profile-guided-optimizations.md)<br/>
Tyto proměnné se používá k určení chování za běhu testování scénářů. Nyní jsou zastaralé a nahrazují nové možnosti linkeru. Tento dokument ukazuje, jak přesunout z proměnných prostředí, možnosti linkeru.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkce můžete přidat do své aplikace a poskytují podrobné `.pgc` ovládací prvek pro zachycení dat souborů.

[pgosweep](pgosweep.md)<br/>
Nástroj příkazového řádku, který zapíše všechna data profilu k `.pgc` souboru, ukončí `.pgc` souborů a otevře se nový `.pgc` souboru.

[pgomgr](pgomgr.md)<br/>
Nástroj příkazového řádku, který přidá data profilu z jedné nebo více `.pgc` soubory `.pgd` souboru.

[Postupy: Sloučení několika profilů PGO do jediného profilu](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Příklady **pgomgr** využití.

## <a name="see-also"></a>Viz také:

[Další nástroje sestavení MSVC](reference/c-cpp-build-tools.md)
