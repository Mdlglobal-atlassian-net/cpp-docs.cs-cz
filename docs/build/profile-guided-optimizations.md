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

Optimalizace na základě profilu (PGO) umožňuje optimalizovat celý spustitelný soubor, kde Optimalizátor používá data z testovacích běhů souboru. exe nebo. dll. Data představují pravděpodobný výkon programu v produkčním prostředí.

Optimalizace na základě profilu jsou k dispozici pouze pro nativní cíle x86 nebo x64. Optimalizace na základě profilu nejsou k dispozici pro spustitelné soubory, které běží v modulu CLR (Common Language Runtime). I když vytváříte sestavení se smíšeným nativním a spravovaným kódem (pomocí možnosti kompilátoru **/CLR** ), nemůžete použít optimalizaci na základě profilu na pouze nativní kód. Pokud se pokusíte sestavit projekt s těmito možnostmi nastavenými v integrovaném vývojovém prostředí (IDE), dojde k chybě sestavení.

> [!NOTE]
> Informace, které se shromažďují z testovacích běhů, potlačí optimalizace, které by jinak vstoupily v platnost, pokud zadáte **/ob**, **/OS**nebo **/ot**. Další informace naleznete v tématu [/ob (rozšíření vložené funkce)](reference/ob-inline-function-expansion.md) a [/OS,/ot (upřednostnění malého kódu, upřednostnění rychlého kódu)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Postup optimalizace aplikace

Pokud chcete použít optimalizaci na základě profilu, postupujte podle těchto kroků a optimalizujte svou aplikaci:

- Zkompilujte jeden nebo více souborů zdrojového kódu s [/GL](reference/gl-whole-program-optimization.md).

   Každý modul sestavený s **/GL** lze prozkoumat během testovacích běhů s profilací na základě profilu, který zachytí chování za běhu. Každý modul v sestavení optimalizace na základě profilu není nutné kompilovat s **/GL**. Pro optimalizace na základě profilu jsou však instrumentované a později dostupné pouze ty moduly, které jsou zkompilovány s **/GL** .

- Propojení pomocí [/LTCG](reference/ltcg-link-time-code-generation.md) a [/GENPROFILE nebo/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Když použijete **/LTCG** i **/GENPROFILE** nebo **/FASTGENPROFILE** , `.pgd` vytvoří se soubor při spuštění instrumentované aplikace. Po spuštění testu jsou do `.pgd` souboru přidána data, která lze použít jako vstup k dalšímu kroku propojení (vytvoření optimalizované bitové kopie). Při zadávání **/GENPROFILE**můžete volitelně přidat argument **PGD =**_filename_ pro určení nevýchozího názvu nebo umístění `.pgd` souboru. Kombinace možností linkeru **/LTCG** a **/GENPROFILE** nebo **/FASTGENPROFILE** nahrazuje možnost linkeru zastaralou **/LTCG: PGINSTRUMENT** .

- Profilování aplikace.

   Pokaždé, když se ukončí profilovaná relace EXE, nebo je `appname!N.pgc` soubor DLL s profilací uvolněn, vytvoří se soubor. `.pgc` Soubor obsahuje informace o konkrétním testovacím běhu aplikace. *AppName* je název vaší aplikace a *N* je číslo od 1, které se zvyšuje na základě počtu dalších `appname!N.pgc` souborů v adresáři. `.pgc` Soubor můžete odstranit, pokud testovací běh nepředstavuje scénář, který chcete optimalizovat.

   Během testovacího běhu můžete vynutit uzavření aktuálně otevřeného `.pgc` souboru a vytvoření nového `.pgc` souboru pomocí nástroje [pgosweep](pgosweep.md) (například když se konec testovacího scénáře neshoduje s ukončením aplikace).

   Vaše aplikace může také přímo vyvolat funkci PGO, [PgoAutoSweep](pgoautosweep.md)pro zachycení dat profilu v místě volání jako `.pgc` soubor. Může vám poskytnout lepší kontrolu nad kódem, který jsou pokrytá zachycenými daty `.pgc` ve vašich souborech. Příklad použití této funkce najdete v dokumentaci k [PgoAutoSweep](pgoautosweep.md) .

   Když vytvoříte instrumentované sestavení, je shromažďování dat ve výchozím nastavení provedeno v režimu bez bezpečného přístupu z více vláken, což je rychlejší, ale může být nepřesné. Když použijete **přesný** argument pro **/GENPROFILE** nebo **/FASTGENPROFILE**, můžete zadat shromažďování dat v režimu bezpečném pro přístup z více vláken, který je přesnější, ale pomalejší. Tato možnost je k dispozici také v případě, že jste při vytváření instrumentované sestavení nastavili zastaralou proměnnou prostředí [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) nebo možnost linkeru, která je zastaralá **/POGOSAFEMODE** .

- Propojit pomocí **/LTCG** a **/USEPROFILE**.

   K vytvoření optimalizované bitové kopie použijte možnosti linkeru **/LTCG** a [/USEPROFILE](reference/useprofile.md) . Tento krok přijímá jako vstupní `.pgd` soubor. Když zadáte **/USEPROFILE**, můžete volitelně přidat argument **PGD =**_filename_ , který určí jiný než výchozí název nebo umístění `.pgd` souboru. Tento název můžete zadat také pomocí nepoužívaného parametru linkeru **/PGD** . Kombinace parametrů **/LTCG** a **/USEPROFILE** nahrazuje zastaralé **/LTCG: PGOPTIMIZE** a **/LTCG: PGUPDATE** Možnosti linkeru.

Je dokonce možné vytvořit optimalizovaný spustitelný soubor a později určit, že další profilace by byla užitečná pro vytvoření optimalizované bitové kopie. Je-li instrumentovaná image a `.pgd` její soubor k dispozici, můžete provést další testovací běhy a znovu sestavit optimalizovanou bitovou kopii `.pgd` s novějším souborem pomocí stejných možností linkeru **/LTCG** a **/USEPROFILE** .

## <a name="optimizations-performed-by-pgo"></a>Optimalizace prováděné PGO

Optimalizace na základě profilu obsahují tyto kontroly a vylepšení:

- Vložení **– Pokud** je například funkce, která často volá funkci b, a funkce b je poměrně malá, pak optimalizace na základě profilu vloží vloženou funkci b do funkce a.

- **Spekulativní virtuální volání** – Pokud virtuální volání nebo jiné volání prostřednictvím ukazatele na funkci, často cílí na určitou funkci, může optimalizace na základě profilu vložit podmíněně spouštěné přímé volání do často cílené funkce a přímé volání může být vložené.

- **Registrace přidělení** – optimalizace na základě výsledků dat profilu vám umožní lépe přidělit registraci.

- **Optimalizace základního blokování** – optimalizace základních bloků umožňuje běžně spouštět základní bloky, které se v daném rámci v rámci daného rámce budou umístit do stejné sady stránek (umístění). Minimalizuje počet použitých stránek, což minimalizuje nároky na paměť.

- **Optimalizace velikosti a rychlosti** – funkce, ve kterých se program stráví největším časem spuštění, může být optimalizován pro rychlost.

- **Rozložení funkcí** – na základě grafu volání a převedených chování volajícího/volaného se funkce, které jsou v rámci stejné cesty spuštění, umístí do stejné části.

- **Optimalizace podmíněné větve** – s využitím sond hodnot, optimalizace na základě profilu, můžou zjistit, jestli se daná hodnota v příkazu switch používá častěji než jiné hodnoty.  Tuto hodnotu lze pak z příkazu switch odstranit.  Totéž lze provést s `if`... `else` pokyny, kde může Optimalizátor objednat `if`... `else` takže buď blok nebo `if` `else` je umístěn jako první, v závislosti na tom, který blok je častěji true.

- **Oddělený** kód – kód, který není volán během profilování, je přesunut do speciálního oddílu, který je připojen ke konci sady oddílů. Tato část je efektivně zachovaná mimo často používané stránky.

- **Oddělení kódu EH** – protože kód eh je jenom výjimečně spuštěný, může se často přesunout do samostatného oddílu. Je přesunutá, když optimalizace na základě profilu můžou určit, že se výjimky vyskytují jenom při mimořádných podmínkách.

- **Vnitřní funkce paměti** – určuje, jestli se má rozšířit vnitřní nebo nezávislá na tom, jestli je často se volá. Vnitřní objekt lze optimalizovat také na základě velikosti bloku operací přesunutí nebo kopírování.

## <a name="next-steps"></a>Další kroky

Přečtěte si další informace o těchto proměnných prostředí, funkcích a nástrojích, které můžete použít v optimalizacích na základě profilu:

[Proměnné prostředí pro optimalizace na základě profilu](environment-variables-for-profile-guided-optimizations.md)<br/>
Tyto proměnné byly použity k určení chování testovacích scénářů v době běhu. Už jsou zastaralé a nahrazují je novými možnostmi linkeru. V tomto dokumentu se dozvíte, jak přesunout z proměnných prostředí do možností linkeru.

[PgoAutoSweep](pgoautosweep.md)<br/>
Funkce, kterou můžete přidat do aplikace k poskytnutí podrobného řízení sběru dat `.pgc` souborů.

[pgosweep](pgosweep.md)<br/>
Nástroj příkazového řádku, který zapisuje všechna data profilu do `.pgc` souboru, zavře `.pgc` soubor a otevře nový `.pgc` soubor.

[pgomgr](pgomgr.md)<br/>
Nástroj příkazového řádku, který přidává data profilu z jednoho nebo více `.pgc` souborů do `.pgd` souboru.

[Postupy: sloučení více profilů PGO do jednoho profilu](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Příklady využití **pgomgr**

## <a name="see-also"></a>Viz také

[Další nástroje sestavení MSVC](reference/c-cpp-build-tools.md)
