---
title: Optimalizace na základě profilu | Microsoft Docs
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
ms.openlocfilehash: c7d6de281097232b1b8abc10a103af9c186e3550
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379403"
---
# <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

Optimalizace na základě profilu umožňuje optimalizovat výstupní soubor, kde optimalizátor používá data testovacích běhů souboru .exe nebo .dll. Data představují pravděpodobný výkon programu v provozním prostředí.

Optimalizace na základě profilu jsou dostupné pouze pro x86 nebo x64 nativní cíle. Optimalizace na základě profilu nejsou k dispozici pro výstupní soubory, které běží na modulu CLR. I když můžete vytvořit sestavení s smíšený nativního a spravovaného kódu (pomocí **/CLR** – možnost kompilátoru), nejde použít optimalizace na základě profilu pouze nativní kód. Pokud se pokusíte sestavit projekt pomocí těchto možností nastavení v IDE, způsobuje chybu sestavení.

> [!NOTE]
> Informace získané z profilace testovací spouští přepsání optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](../../build/reference/ob-inline-function-expansion.md) a [/Os, /Ot (upřednostnit malý kód, upřednostnit rychlého kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Kroky k optimalizaci aplikace

Optimalizace na základě profilu, postupujte podle těchto kroků k optimalizaci aplikace:

- Zkompilovat jednu nebo více zdrojových souborů kód s [/GL](../../build/reference/gl-whole-program-optimization.md).

   Každý modul vytvořené s **/GL** může být prověřen během optimalizace na základě profilu testovacích bězích k zachycení běhového chování. Každý modulu v sestavení optimalizace na základě profilu nemusí být zkompilovány s **/GL**. Ale pouze tyto moduly kompilovat s **/GL** jsou instrumentované a později k dispozici pro optimalizace na základě profilu.

- Propojit pomocí [/ltgc](../../build/reference/ltcg-link-time-code-generation.md) a [/GENPROFILE nebo /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Pomocí obou **/ltgc** a **/GENPROFILE** nebo **/FASTGENPROFILE** .pgd soubor se vytvoří při spuštění instrumentované aplikace. Po testovacím běhu jsou do souboru .pgd přidána data a lze jej použít jako vstup pro další krok propojování (vytvoření optimalizované bitové kopie). Při zadávání **/GENPROFILE**, můžete přidat **PGD =**_filename_ argument zadejte jiný než výchozí název nebo umístění souboru .pgd. Kombinace **/ltgc** a **/GENPROFILE** nebo **/FASTGENPROFILE** nahrazuje zastaralé – možnosti linkeru **/LTCG:PGINSTRUMENT** – možnost linkeru.

- Profilování aplikace.

   Pokaždé, když PROFILOVANÉHO EXE relace je ukončena, nebo je odpojen, PROFILOVANÉHO knihovny DLL *appname*! # .pgc soubor je vytvořen. Soubor .pgc obsahuje informace o konkrétním testovacím běhu aplikace. # je číslo od 1, který je zvýšena na základě počtu dalších *appname*! # .pgc souborů v adresáři. Nepředstavuje-li testovací běh scénář, který má být optimalizován, lze soubor .pgc odstranit.

   Během testu, spuštění, můžete vynutit uzavření souboru aktuálně otevřených .pgc a vytvoření nového souboru .pgc s [pgosweep –](../../build/reference/pgosweep.md) nástroj (například když konec scénář testu se neshoduje s ukončení aplikace).

   Aplikace můžete také přímo vyvolat funkci PGO [PgoAutoSweep](pgoautosweep.md), k zaznamenání dat profilu v místě volání jako soubor .pgc. To vám může poskytnout přesnější kontrolu nad kód předmětem zaznamenaná data v souborech .pgc. Příklad toho, jak tuto funkci použít, naleznete v části [PgoAutoSweep](pgoautosweep.md) dokumentaci.

   Když vytvoříte instrumentovaného sestavení, ve výchozím nastavení, shromažďování dat se provádí v režimu není bezpečná pro přístup z více vláken, který je rychlejší, ale nemusí být zcela přesné. Pomocí **EXACT** argument **/GENPROFILE** nebo **/FASTGENPROFILE**, shromažďování dat můžete zadat v režimu bezpečné pro přístup z více vláken, který je přesnější ale pomalejší. Tato možnost je k dispozici, pokud jste nastavili nepoužívané [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) proměnné prostředí, nebo zastaralé **/POGOSAFEMODE** – možnost linkeru, když vytvoříte instrumentovaného buildu.

- Propojit pomocí **/ltgc** a **/USEPROFILE**.

   Použití **/ltgc** a [/USEPROFILE](useprofile.md) možnosti linkeru vytvoření optimalizované bitové kopie. Vstupem pro tento krok je soubor .pgd. Pokud zadáte **/USEPROFILE**, můžete přidat **PGD =**_filename_ argument určit jiné než výchozí název nebo umístění souboru .pgd. Tento název můžete přímo zadat pomocí nepoužívané **/PGD** – možnost linkeru. Kombinace **/ltgc** a **/USEPROFILE** nahrazuje nepoužívané **/LTCG:PGOPTIMIZE** a **/LTCG:PGUPDATE** možnosti linkeru.

Lze dokonce vytvořit optimalizovaný výstupní soubor a později určit, že pro vytvoření více optimalizované bitové kopie by bylo užitečné další profilování. Pokud instrumentovaného bitové kopie a jeho .pgd souboru jsou k dispozici, můžete provést další testovací spouští a znovu vytvořit bitovou kopii optimalizované novější .pgd souborem, pomocí stejné **/ltgc** a **/USEPROFILE** možnosti linkeru .

## <a name="optimizations-performed-by-pgo"></a>Optimalizace provádí PGO

Následuje seznam optimalizací na základě profilu:

- **Vložené** – například, pokud existuje funkce A zda často volání funkce B a funkce B je poměrně malý, a optimalizace na základě profilu bude vložená funkce B ve funkci A.

- **Virtuální volání spekulativní** – Pokud virtuální volání nebo jiné volání prostřednictvím ukazatel na funkci často cílí určité funkce, optimalizace na základě profilu můžete vložit podmíněně provést přímé volání funkce často cílem a přímé volání může být vložená.

- **Přidělení registru** – optimalizace s výsledky data profilu v lepší přidělení registru.

- **Základní optimalizace bloku** – základní blok optimalizace umožňuje běžně spuštění základní bloků, které dočasně provést v rámci dané se mají umístit na stejnou sadu stránek (poloha). Tím je minimalizován počet použitých stránek, a tedy i zatížení paměti.

- **Velikost rychlost optimalizace** – funkce, které program tráví mnoho času lze optimalizovat pro rychlost.

- **Funkce rozložení** – založená na volání grafu a profilovaným volající/volaný chování funkce, které jsou obvykle podle stejné cesty, provádění se umístí do stejné části.

- **Podmíněné optimalizace větve** – s sondy hodnota, na základě profilu optimalizace najdete, pokud se dané hodnoty v příkazu switch používá častěji než ostatní hodnoty.  Tuto hodnotu lze pak z příkazu switch odstranit.  Totéž lze provést s instrukcemi if/else, kde optimalizátor může příkaz if/else uspořádat tak, že je jako první umístěn blok if nebo else v závislosti na tom, který z nich je častěji vyhodnocen na hodnotu true.

- **Neaktivní oddělení kódu** -kód, který není volán při vytváření profilu je přesunuta do speciální oddíl, který je připojen na konec sadu oddíly. Tím je tento oddíl efektivně udržován mimo často používané stránky.

- **EH kód oddělení** -EH kódu, výjimečně vykonáván, můžete často přesunout do samostatné části při optimalizace na základě profilu můžete určit, že výjimky dojít pouze na výjimečných podmínek.

- **Vnitřní funkce paměti** – vnitřní funkce rozšíření lze lépe rozhodnout, pokud může určit, pokud se vnitřní nazývá často. Vnitřní objekt lze optimalizovat také na základě velikosti bloku operací přesunutí nebo kopírování.

Pokud používáte Visual Studio 2013, můžete použít automatizované [Plug-In optimalizace na základě profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) pro Visual C++ v výkon a diagnostiku pro zjednodušení a společně Zjednodušte proces optimalizace v sadě Visual Studio. Tento modul plug-in není k dispozici v novějších verzích sady Visual Studio.

## <a name="next-steps"></a>Další kroky

Další informace o těchto proměnných prostředí, funkce a nástroje, které můžete použít v optimalizace na základě profilu:

[Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Tyto proměnné můžete použít k určení chování testování scénáře. Jsou zastaralé považuje nové možnosti linkeru; To můžete přesunout z proměnných prostředí, možnosti linkeru přečíst.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkce, které přidáte do své aplikace a poskytují podrobné .pgc ovládací prvek zachycení dat souborů.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Nástroj příkazového řádku, který zapíše všechna data profilu do souboru .pgc soubor .pgc se zavře a otevře nový soubor .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Nástroj příkazového řádku, který přidá data profilu z jednoho nebo více souborů .pgc .pgd souboru.

[Postupy: sloučení několika profilů PGO do jediného profilu](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md) příklady **pgomgr –** využití.

## <a name="see-also"></a>Viz také

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)
