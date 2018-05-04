---
title: /MP (sestavení pomocí několika procesů) | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
dev_langs:
- C++
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29f7fd00a9d24b1941830690633befc75c39eb32
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mp-build-with-multiple-processes"></a>/MP (sestavení pomocí několika procesů)

**/MP** možnost může snížit celkovou dobu kompilace zdrojových souborů na příkazovém řádku. **/MP** možnost způsobí, že kompilátor vytvoří jednu nebo více kopií sám sebe, každý samostatný proces. Potom tyto kopie současně zkompilovat zdrojové soubory. V důsledku toho může být výrazně snížit celkový čas k sestavení zdrojových souborů.

## <a name="syntax"></a>Syntaxe

> **/MP**[*processMax*]

## <a name="arguments"></a>Arguments

*processMax*<br/>
(Volitelné) Maximální počet procesů, které můžete vytvořit kompilátoru.

*ProcessMax* argument musí být v rozsahu od 1 až 65536. Jinak, vydá upozornění **D9014**, ignoruje *processMax* argument a předpokládá 1 je maximální počet procesů.

V případě vynechání *processMax* argument, kompilátor načte počet [efektivní procesory](#effective_processors) ve vašem počítači z operačního systému a vytvoří proces pro každý procesor.

## <a name="remarks"></a>Poznámky

**/MP** – možnost kompilátoru můžete výrazně zkrátit čas sestavení při kompilaci mnoho souborů. Pro zlepšení čase vytvoření buildu, kompilátor vytvoří až *processMax* zkopíruje sám sebe a pak používá tyto kopie zkompilovat zdrojové soubory ve stejnou dobu. **/MP** možnost se vztahuje na kompilace, ale ne na serveru linking nebo propojování generování kódu. Ve výchozím nastavení **/MP** možnost je vypnuta.

Zlepšování v čase vytvoření buildu závisí na počet procesorů v počítači, počet souborů ke kompilaci a dostupnost prostředky systému, například v/v kapacitu. Experimentujte s **/MP** možnost určit doporučené nastavení pro konkrétní projekt sestavit. Rady, jak vám pomůže provádět rozhodnutí, najdete v části [pokyny](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Nekompatibilní možnosti a funkce jazyka

**/MP** možnost není kompatibilní s některými – možnosti kompilátoru a jazyk funkce. Pokud použijete možnost nekompatibilní kompilátoru s **/MP** možnost, vydá upozornění **D9030** a ignoruje **/MP** možnost. Pokud používáte funkci nekompatibilní jazyk, kompilátor vyvolá chybu [C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) a končí, nebo pokračuje v závislosti na aktuální kompilátoru upozornění úrovně možnost.

> [!NOTE]
> Většina možností nejsou kompatibilní, protože pokud jejich měla povoleno, souběžně spuštěných kompilátory by zápis jejich výstup ve stejnou dobu, na konzole nebo do konkrétního souboru. V důsledku toho výstup by kombinovat a být poškozen. V některých případech by kombinace možností zkontrolujte nejhorší výkonu.

Následující tabulka uvádí možnosti kompilátoru a jazyk funkce, které jsou kompatibilní s **/MP** možnost:

|Možnosti nebo funkce jazyka|Popis|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) direktivy preprocesoru|Převede typy v knihovně typu třídy jazyka C++ a pak tyto třídy zapisuje do souboru záhlaví.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Výstup preprocesoru zkopíruje do standardního výstupního (**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Umožňuje přírůstkové opětovné sestavení.|
|[/ showincludes vložených](../../build/reference/showincludes-list-include-files.md)|Zapíše seznam zahrnout soubory do standardního chybového (**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Zapíše předkompilovaný hlavičkový soubor.|

## <a name="diagnostic-messages"></a>Diagnostické zprávy

Pokud zadáte funkce možnost nebo jazyk, který je nekompatibilní s **/MP** možnost, obdržíte zprávu diagnostiky. Následující tabulka uvádí zprávy a chování kompilátoru:

|Diagnostické zprávy|Popis|Chování kompilátoru|
|------------------------|-----------------|-----------------------|
|**C2813**|**#Import** – direktiva není kompatibilní s **/MP** možnost.|Kompilace ukončí, pokud [úroveň pro upozornění kompilátoru](../../build/reference/compiler-option-warning-level.md) možnost neurčí jinak.|
|**D9014**|Je zadaná neplatná hodnota pro *processMax* argument.|Kompilátor ignoruje neplatnou hodnotu a předpokládá hodnotu 1.|
|**D9030**|Zadaná možnost není kompatibilní s **/MP**.|Kompilátor ignoruje **/MP** možnost.|

## <a name="guidelines"></a> Pokyny

### <a name="measure-performance"></a>Míra výkonu

Použijte sestavení celkový čas k měření výkonu. Čas sestavení můžete měřit s fyzické hodinami, nebo můžete použít software, který vypočítá rozdíl mezi při sestavení spuštění a zastavení. Pokud má počítač více procesorů, může být fyzické hodiny poskytují přesnější výsledky než čas měření softwaru.

### <a name="effective_processors"></a> Efektivní procesorů

V počítači může být jeden nebo více virtuálních procesorů, které se také označují jako *efektivní procesory*, pro každý z jeho fyzických procesorů. Každý fyzického procesoru může mít jeden nebo více jader, a pokud operačního systému umožňuje hyperthreading pro jádro, každý základní se zdá být dva virtuální procesory.

Například počítač má jeden efektivní procesor, pokud má jedna fyzického procesoru, který má jednoho jádra a Hyper-threadingem, je zakázán. Počítač, naproti tomu má osm efektivní procesorů, pokud má dva fyzické procesory, z nichž každá má dvě jádra, a všechna jádra máte povoleným Hyper-threadingem. To znamená (8 efektivní procesory) = (2 fyzických procesorů) x (2 jádra za fyzického procesoru) x (2 efektivní procesorů na základní kvůli Hyper-threadingem).

Pokud vynecháte *processMax* argument ve **/MP** možnost kompilátor získá počet procesorů efektivní z operačního systému a potom vytvoří jeden proces na efektivní procesor. Kompilátor však nemůže zaručit, který proces provede konkrétní procesoru; operační systém provádí tohoto rozhodnutí.

### <a name="number-of-processes"></a>Počet procesů

Kompilátor vypočítá počet procesů, které se bude používat pro kompilaci zdrojové soubory. Hodnota je menší počet zdrojové soubory, které zadáte v příkazovém řádku a počet procesů, které explicitně nebo implicitně zadáte pomocí **/MP** možnost. Pokud zadáte můžete explicitně nastavit maximální počet procesů *processMax* argument **/MP** možnost. Nebo můžete použít výchozí, což je stejný jako počet efektivní procesorů v počítači, v případě vynechání *processMax* argument.

Předpokládejme například, že zadáte následující příkaz:

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

V takovém případě kompilátor používá pět procesy, protože takové je menší z pěti zdrojové soubory a nesmí být delší než sedm procesy. Nebo Předpokládejme v počítači dva procesory efektivní a zadejte následující příkaz:

`cl /MP a.cpp b.cpp c.cpp`

V takovém případě operační systém sestavy dva procesory; Proto kompilátor používá dva procesy v jeho výpočtu. V důsledku toho kompilátor provede sestavení pomocí dvou procesů, protože takové je menší dva procesy a tři zdrojové soubory.

### <a name="source-files-and-build-order"></a>Zdrojové soubory a pořadí sestavení

Zdrojové soubory, nemusí být zkompilovány ve stejném pořadí, ve kterém se zobrazí na příkazovém řádku. I když kompilátor vytvoří sadu procesy, které obsahují kopie kompilátor, operačního systému plánuje když provede jednotlivých procesů. V důsledku toho nemůže zaručit, že se zkompiluje zdrojové soubory v určitém pořadí.

Zdrojový soubor je kompilovat, pokud je k dispozici kompilování proces. Pokud existují další soubory než procesy, je k dispozici procesy zkompilovat první sadu souborů. Zbývající soubory jsou zpracovat, když proces dokončí zpracování předchozí souboru a je k dispozici pro práci na jednom z zbývající soubory.

Nezadávejte stejné zdrojový soubor vícekrát na příkazovém řádku. Této chybě může dojít, například nástroj automaticky vytvoří [makefile](../../build/contents-of-a-makefile.md) založený na informace o závislostech v projektu. Pokud nezadáte **/MP** možnost kompilátor postupně zpracovává seznam souborů a znovu zkompiluje každý výskyt souboru. Ale pokud zadáte **/MP** možnost, jiný kompilátory může kompilovat stejný soubor ve stejnou dobu. Různé kompilátory v důsledku toho se pokusí zapisovat do stejného souboru výstup ve stejnou dobu. Jeden kompilátoru se získat výhradní přístup k zápisu do výstupního souboru a úspěšné a jinými kompilátory se nezdaří s chyba přístupu k souboru.

### <a name="using-type-libraries-import"></a>Použití knihoven typů (#import)

Kompilátor nepodporuje použití [#import](../../preprocessor/hash-import-directive-cpp.md) direktivy s **/MP** přepínače. Pokud je to možné použijte následující postup tento problém vyřešit:

- Přesouvání všech `#import` direktivy ve vašem různé zdrojových souborů na jeden nebo více souborů a pak zkompilovat tyto soubory bez **/MP** možnost. Výsledkem je sadu soubory generované hlaviček.

- Ve vašem zbývající zdrojové soubory, vložte [#include](../../preprocessor/hash-include-directive-c-cpp.md) direktivy, které zadejte vygenerované hlavičky a pak zkompilovat váš zbývající zdrojové soubory pomocí **/MP** možnost.

### <a name="visual-studio-project-settings"></a>Nastavení projektu sady Visual Studio

#### <a name="the-msbuildexe-tool"></a>Nástroje MSBUILD.exe

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] používá [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) nástroj pro vývoj řešení a projekty. **/Maxcpucount:**_číslo_ (nebo **/m:**_číslo_) možnost příkazového řádku nástroje MSBuild.exe můžete vytvořit více projektů v stejnou dobu. A **/MP** – možnost kompilátoru můžete vytvořit několika kompilačních jednotek ve stejnou dobu. Pokud je vhodné pro vaši aplikaci, můžete zlepšit použitím jedné nebo obou čase vytvoření buildu vaše řešení **/MP** a **/maxcpucount**.

Čas sestavení řešení závisí částečně na počet procesů, které provádějí sestavení. *Číslo* argument [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild možnost určuje maximální počet projekty k sestavení ve stejnou dobu. Podobně *processMax* argument **/MP** – možnost kompilátoru určuje maximální počet jednotek kompilace vytvářet ve stejnou dobu. Pokud **/maxcpucount** možnost určuje *P* projekty a **/MP** možnost určuje *C* zpracovává, nesmí být delší než *P*  x *C* procesy spuštění ve stejnou dobu.

 Platí pro rozhodování, jestli se má používat nástroje MSBuild nebo **/MP** technologie vypadá takto:

- Pokud existují mnoha projektů u některých souborů v každém projektu, pomocí nástroje MSBuild.

- Pokud nejsou k dispozici několik projekty s mnoha souborech v každém projektu, použijte **/MP** možnost.

- Pokud jsou rovnoměrně počet projekty a souborů na projekt, použijte MSBuild a **/MP**. Zpočátku nastavena **/maxcpucount** možnost počet projekty k sestavení a **/MP** možnost počet procesorů v počítači. Měření výkonu a budou nastavení poskytují nejlepší výsledky. Opakujte tento cyklus, dokud nebudete přesvědčeni s časem celkový sestavení.

#### <a name="the-gm-compiler-option"></a>/Gm – možnost kompilátoru

Ve výchozím nastavení, sestavení projektu umožňuje **/Gm** – možnost kompilátoru (přírůstkové sestavení) pro sestavení pro ladění a zakáže pro verzi sestavení. Proto **/MP** – možnost kompilátoru je automaticky zakázán u sestavení ladicí verze, protože je v konfliktu s výchozí **/Gm** – možnost kompilátoru.

## <a name="see-also"></a>Viz také

[#import – direktiva](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Referenční dokumentace k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf (rychlejší generování souborů PDB)](zf.md)<br/>
