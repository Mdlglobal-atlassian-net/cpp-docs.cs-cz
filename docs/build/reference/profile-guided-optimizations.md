---
title: "Optimalizace na základě profilu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2d72ddda460a88830f7f7692f4c9707fa3101a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu
Optimalizace na základě profilu umožňuje optimalizovat výstupní soubor, kde optimalizátor používá data testovacích běhů souboru .exe nebo .dll. Data představují pravděpodobný výkon programu v provozním prostředí.  
  
 Optimalizace na základě profilu jsou dostupné pouze pro nativní cíle x86 nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]. Optimalizace na základě profilu nejsou dostupné pro výstupní soubory, které budou spuštěny v modulu Common Language Runtime. I když můžete vytvořit sestavení s smíšený nativního a spravovaného kódu (Kompilovat s **/CLR**), nejde použít jenom nativní kód optimalizace na základě profilu. Pokusíte-li se sestavit projekt s těmito možnostmi nastavenými v prostředí IDE, dojde k chybě sestavení.  
  
> [!NOTE]
>  Informace získané z profilace testovací spouští přepíší optimalizace, které by jinak byly v vliv, pokud zadáte **/Ob**, **/Os**, nebo **/Ot**. Další informace najdete v tématu [/Ob (rozbalení vložené funkce)](../../build/reference/ob-inline-function-expansion.md) a [/Os, /Ot (upřednostnit malý kód, upřednostnit rychlého kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).  
  
 Automatizované optimalizace na základě profilu můžete použít pro Visual C++ v výkon a diagnostiku modulu plug-in pro zjednodušení a společně Zjednodušte proces optimalizace v sadě Visual Studio, nebo můžete provést kroky optimalizace ručně v sadě Visual Studio nebo na příkazový řádek. Doporučujeme Modul plug-in, protože je jednodušší použít. Informace o tom, jak získat modul plug-in a použít ho k optimalizaci aplikace najdete v tématu [Plug-In optimalizace na základě profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
 Obě optimalizace na základě profilu modulů plug-in a ruční optimalizace na základě profilu použijte následující postup optimalizace aplikace:  
  
-   Zkompilovat jednu nebo více zdrojových souborů kód s [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
     Všechny moduly sestavené s možností /GL budou během testovacích běhů optimalizace na základě profilu přezkoumány a bude zachyceno jejich chování za běhu. Ne všechny moduly v sestavení optimalizace na základě profilu musí být zkompilovány s možností /GL. Avšak pouze moduly zkompilované s možností /GL budou instrumentovány a později dostupné pro optimalizace na základě profilu.  
  
-   Propojit pomocí [/ltgc](../../build/reference/ltcg-link-time-code-generation.md) a [/GENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).  
  
     Pomocí/ltgc a /GENPROFILE vytvoří soubor prázdný .pgd. Po testovacím běhu jsou do souboru .pgd přidána data a lze jej použít jako vstup pro další krok propojování (vytvoření optimalizované bitové kopie). Při zadávání /GENPROFILE, můžete přidat: PGD =`filename` určete jiný než výchozí název nebo umístění souboru .pgd.  
  
-   Profilování aplikace.  
  
     Pokaždé, když PROFILOVANÉHO EXE relace je ukončena, nebo je odpojen, PROFILOVANÉHO knihovny DLL *appname*! # .pgc soubor je vytvořen. Soubor .pgc obsahuje informace o konkrétním testovacím běhu aplikace. # je číslo od 1, který je zvýšena na základě počtu dalších *appname*! # .pgc souborů v adresáři. Nepředstavuje-li testovací běh scénář, který má být optimalizován, lze soubor .pgc odstranit.  
  
     Během testu, spuštění, můžete vynutit uzavření souboru aktuálně otevřených .pgc a vytvoření nového souboru .pgc s [pgosweep –](../../build/reference/pgosweep.md) nástroj (například když konec scénář testu se neshoduje s ukončení aplikace).  
  
     Při profilování aplikace lze použít možnost `PogoSafeMode`. Tato možnost umožňuje určit, zda chcete profilovat aplikaci v bezpečném nebo rychlém režimu. Další informace o těchto režimech najdete v tématu [PogoSafeMode](../../build/reference/pogosafemode.md).  
  
-   Propojte pomocí/ltgc a /USEPROFILE.  
  
     Pomocí/ltgc a /USEPROFILE vytvoří bitovou kopii optimalizované. Vstupem pro tento krok je soubor .pgd. Při zadávání /USEPROFILE, můžete přidat: PGD =`filename` určete jiný než výchozí název nebo umístění souboru .pgd. Další informace najdete v tématu [/ltgc](../../build/reference/ltcg-link-time-code-generation.md).  
  
 Lze dokonce vytvořit optimalizovaný výstupní soubor a později určit, že pro vytvoření více optimalizované bitové kopie by bylo užitečné další profilování. Je-li instrumentovaná bitová kopie a její soubor .pgd k dispozici, lze provést dodatečné testovací běhy a optimalizovanou bitovou kopii znovu sestavit s novým souborem .pgd.  
  
 Následuje seznam optimalizací na základě profilu:  
  
-   **Vložené** – například, pokud existuje funkce A zda často volání funkce B a funkce B je poměrně malý, a optimalizace na základě profilu bude vložená funkce B ve funkci A.  
  
-   **Virtuální volání spekulativní** – Pokud virtuální volání nebo jiné volání prostřednictvím ukazatel na funkci často cílí určité funkce, optimalizace na základě profilu můžete vložit podmíněně provést přímé volání funkce často cílem a přímé volání může být vložená.  
  
-   **Přidělení registru** – optimalizace s výsledky data profilu v lepší přidělení registru.  
  
-   **Základní optimalizace bloku** – základní blok optimalizace umožňuje běžně spuštění základní bloků, které dočasně provést v rámci dané se mají umístit na stejnou sadu stránek (poloha). Tím je minimalizován počet použitých stránek, a tedy i zatížení paměti.  
  
-   **Velikost rychlost optimalizace** – funkce, které program tráví mnoho času lze optimalizovat pro rychlost.  
  
-   **Funkce rozložení** – založená na volání grafu a profilovaným volající/volaný chování funkce, které jsou obvykle podle stejné cesty, provádění se umístí do stejné části.  
  
-   **Podmíněné optimalizace větve** – s sondy hodnota, na základě profilu optimalizace najdete, pokud se dané hodnoty v příkazu switch používá častěji než ostatní hodnoty.  Tuto hodnotu lze pak z příkazu switch odstranit.  Totéž lze provést s instrukcemi if/else, kde optimalizátor může příkaz if/else uspořádat tak, že je jako první umístěn blok if nebo else v závislosti na tom, který z nich je častěji vyhodnocen na hodnotu true.  
  
-   **Neaktivní oddělení kódu** -kód, který není volán při vytváření profilu je přesunuta do speciální oddíl, který je připojen na konec sadu oddíly. Tím je tento oddíl efektivně udržován mimo často používané stránky.  
  
-   **EH kód oddělení** -EH kódu, výjimečně vykonáván, můžete často přesunout do samostatné části při optimalizace na základě profilu můžete určit, že výjimky dojít pouze na výjimečných podmínek.  
  
-   **Vnitřní funkce paměti** – vnitřní funkce rozšíření lze lépe rozhodnout, pokud může určit, pokud se vnitřní nazývá často. Vnitřní objekt lze optimalizovat také na základě velikosti bloku operací přesunutí nebo kopírování.  
  
 Další informace o provádění ruční optimalizace v prostředí IDE nebo na příkazovém řádku najdete v tématu [Plug-In optimalizace na základě profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Modul Plug-In optimalizace na základě profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [Nástroje pro ruční optimalizace na základě profilu](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [Postupy: Sloučení několika profilů PGO do jediného profilu](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)