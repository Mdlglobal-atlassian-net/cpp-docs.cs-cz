---
title: /MP (sestavení pomocí několika procesů)
ms.date: 02/22/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
ms.openlocfilehash: 8a66f6f6f1f4ce77e33df992b915be9ca5dcce70
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808453"
---
# <a name="mp-build-with-multiple-processes"></a>/MP (sestavení pomocí několika procesů)

**/MP** možnost, jak můžete snížit celkový čas kompilace zdrojových souborů na příkazovém řádku. **/MP** možnost způsobí, že kompilátor vytvoří jednu nebo více kopií sebe sama, každou v samostatném procesu. Kompilujte ho tyto kopie současně zdrojové soubory. V důsledku toho celková doba nutná k sestavení zdrojových souborů může výrazně snížit.

## <a name="syntax"></a>Syntaxe

> **/MP**[*processMax*]

## <a name="arguments"></a>Arguments

*processMax*<br/>
(Volitelné) Maximální počet procesů, které můžete vytvořit kompilátor.

*ProcessMax* argument musí být v rozsahu od 1 do 65536. V opačném případě kompilátor vyvolá upozornění **D9014**, ignoruje *processMax* argument a které předpokládá 1 je maximální počet procesů.

Vynecháte-li *processMax* argumentů, kompilátor zjišťuje počet [efektivní procesorů](#effective_processors) ve vašem počítači v operačním systému a vytvoří proces pro každý procesor.

## <a name="remarks"></a>Poznámky

**/MP** – možnost kompilátoru můžete výrazně zkrátit čas sestavení, pokud kompilujete mnoho souborů. Pokud chcete zlepšit dobu sestavení, kompilátor vytvoří až *processMax* zkopíruje sám sebe a pak používá tyto kopie pro kompilaci souborů se zdrojovým ve stejnou dobu. **/MP** možnost se vztahuje k kompilace, ale ne k propojení nebo propojování generování kódu. Ve výchozím nastavení **/MP** možnost je vypnuta.

Zvýšení doby sestavení závisí na počtu procesorů v počítači, počet souborů ke kompilaci a dostupnost systémové prostředky, jako je například vstupně-výstupní kapacity. Vyzkoušet **/MP** možnost určit je doporučené nastavení pro konkrétní projekt sestavit. Doporučení, která vám pomůže zajistit rozhodnutí, naleznete v tématu [pokyny](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Nekompatibilní možnosti a funkce jazyka

**/MP** možnost není kompatibilní s některé možnosti kompilátoru a jazyk funkce. Pokud použijete možnost kompilátoru kompatibilní s **/MP** možnost, kompilátor vyvolá upozornění **D9030** a ignoruje **/MP** možnost. Pokud používáte funkci nekompatibilní jazyk, kompilátor vydává chybu [C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) pak skončí nebo pokračuje v závislosti na aktuální upozornění úrovně – možnost kompilátoru.

> [!NOTE]
> Většinu možností nejsou kompatibilní, protože pokud byly převody povoleny, souběžně prováděným kompilátory by zapisují svůj výstup ve stejnou dobu, do konzoly nebo do konkrétního souboru. V důsledku toho výstup by kombinovat a být poškozen. V některých případech kombinace parametrů s žádným horší výkon.

Následující tabulka uvádí možnosti kompilátoru a funkce jazyka, které nejsou kompatibilní s **/MP** možnost:

|Možnosti nebo funkce jazyka|Popis|
|--------------------------------|-----------------|
|[#import](../../preprocessor/hash-import-directive-cpp.md) direktivy preprocesoru|Převede typy v knihovně typů na třídy jazyka C++ a pak zapíše do souboru hlaviček těchto tříd.|
|[/E](e-preprocess-to-stdout.md), [/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Zkopíruje výstup předzpracování do standardního výstupu (**stdout**).|
|[/Gm](gm-enable-minimal-rebuild.md)|Umožňuje přírůstkové sestavení.|
|[/showIncludes](showincludes-list-include-files.md)|Zapíše seznam vložených souborů do standardní chyby (**stderr**).|
|[/Yc](yc-create-precompiled-header-file.md)|Zapíše soubor předkompilované hlavičky.|

## <a name="diagnostic-messages"></a>Diagnostické zprávy

Pokud určíte funkci možnost v jakémkoli jazyce, který není kompatibilní s **/MP** možnost, zobrazí se diagnostické zprávy. V následující tabulce jsou uvedeny zprávy a chování kompilátoru:

|Diagnostické zprávy|Popis|Chování kompilátoru|
|------------------------|-----------------|-----------------------|
|**C2813**|**#Import** – direktiva není kompatibilní s **/MP** možnost.|Kompilace se ukončí, není-li [úroveň upozornění kompilátoru](compiler-option-warning-level.md) možnost neurčí jinak.|
|**D9014**|Zadána neplatná hodnota pro *processMax* argument.|Kompilátor ignoruje neplatnou hodnotu a předpokládá hodnotu 1.|
|**D9030**|Zadaná možnost není kompatibilní s **/MP**.|Kompilátor ignoruje **/MP** možnost.|

## <a name="guidelines"></a> Pokyny

### <a name="measure-performance"></a>Měření výkonu

Čas celkový počet sestavení použijte k měření výkonu. Dobu sestavení lze změřit s fyzickou hodinami, nebo můžete použít software, který vypočítá rozdíl mezi při sestavení spustí a zastaví. Pokud má počítač více procesorů, fyzické hodiny může poskytnout přesnější výsledky než čas měření softwaru.

### <a name="effective_processors"></a> Efektivní procesorů

Počítač může mít jednu nebo víc virtuálních procesorů, které se také označují jako *efektivní procesorů*, pro každý z jeho fyzické procesory. Každý fyzický procesor může mít jeden nebo více jader, a pokud operačního systému umožňuje hyperthreading pro jádro, každé jádro se zdá být dva virtuální procesory.

Třeba počítač má jeden procesor efektivní, pokud má jedna fyzického procesoru, která má jedno jádro a hyperthreadingem je zakázaná. Naproti tomu počítač má osm procesorů efektivní, pokud má dva fyzické procesory, z nichž každá má dvě jádra, a povoleným hyperthreadingem máte všechna jádra. To znamená (8 procesorů efektivní) = (2 fyzických procesorů) x (2 jádra na fyzický procesor) x (2 platit podle počtu jader kvůli hyperthreadingem procesory).

Vynecháte-li *processMax* argumentu **/MP** možnost, kompilátor získá počet procesorů, efektivní z operačního systému a pak vytvoří jeden proces za účinné procesoru. Kompilátor však nemůže zaručit, který proces spustí na konkrétním procesoru; operační systém provede rozhodnutí.

### <a name="number-of-processes"></a>Počet procesů

Kompilátor vypočítá počet procesů, které se bude používat pro kompilaci zdrojové soubory. Hodnota je menší než počet zdrojových souborů, které zadáte v příkazovém řádku a počet procesů, která je explicitně nebo implicitně zadat s **/MP** možnost. Můžete explicitně nastavit maximální počet procesů, pokud zadáte *processMax* argument **/MP** možnost. Nebo můžete použít výchozí, což se rovná počtu procesorů efektivní v počítači, pokud vynecháte *processMax* argument.

Předpokládejme například, že zadáte následující příkaz:

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

V tomto případě kompilátor používá pět procesy vzhledem k tomu, který je menší než pět zdrojových souborů a maximálně sedm procesy. Také Předpokládejme, že váš počítač má dva procesory efektivní a zadat následující příkazový řádek:

`cl /MP a.cpp b.cpp c.cpp`

V tomto případě operační systém ohlásí dva procesory; Proto kompilátor používá dva procesy v provádění výpočtu. V důsledku toho kompilátor bude spustit sestavení pomocí dvou procesů, protože, která je menší než délka dvou procesy a tři zdrojové soubory.

### <a name="source-files-and-build-order"></a>Zdrojové soubory a pořadí sestavení

Zdrojové soubory nemusí být zkompilovány ve stejném pořadí, v jakém jsou uvedeny v příkazovém řádku. Ačkoli kompilátor vytvoří sadu procesy, které obsahují kopie kompilátor, operačního systému plánuje když každý proces spuštěn. V důsledku toho nemůže zaručit, že se zkompiluje zdrojové soubory v určitém pořadí.

Zdrojový soubor je zkompilován, když není k dispozici pro jeho kompilaci proces. Pokud existují další soubory než procesy, první sadu souborů je zkompilován s procesy k dispozici. Zbývající soubory se zpracovávají, pokud proces dokončí zpracování předchozí soubor a je k dispozici pro práci na jednom ze zbývajících souborů.

Nezadávejte stejném zdrojovém souboru více než jednou v příkazovém řádku. Tato situace může nastat, například, pokud nástroj automaticky vytváří [makefile](contents-of-a-makefile.md) , který je založen na informace o závislostech v projektu. Pokud nezadáte **/MP** možnost, kompilátor zpracovává seznam souborů, které postupně a znovu zkompiluje každý výskyt souboru. Nicméně pokud zadáte **/MP** možnost, různými kompilátory může stejný soubor zkompilovat ve stejnou dobu. V důsledku toho různými kompilátory pokusí se zapsat do stejného výstupního souboru ve stejnou dobu. Jeden kompilátoru se získat výhradní přístup pro zápis do výstupního souboru a úspěšné, a jinými kompilátory se nezdaří s chybou přístup k souboru.

### <a name="using-type-libraries-import"></a>Použití knihoven typů (#import)

Kompilátor nepodporuje použití [#import](../../preprocessor/hash-import-directive-cpp.md) s **/MP** přepnout. Pokud je to možné použijte následující postup tento problém vyřešit:

- Přesunout všechny `#import` direktivy vaše různá zdrojové soubory pro jeden nebo více souborů a potom zkompilujete tyto soubory bez **/MP** možnost. Výsledkem je sadu generovanou hlavičkou souborů.

- Ve zbývající zdrojové soubory, vložte [#include](../../preprocessor/hash-include-directive-c-cpp.md) direktivy, které specifikují generované záhlaví a následnou kompilaci zbývající zdrojové soubory s použitím **/MP** možnost.

### <a name="visual-studio-project-settings"></a>Nastavení projektu Visual Studio

#### <a name="the-msbuildexe-tool"></a>Nástroj MSBUILD.exe

Visual Studio používá [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) nástroj pro sestavování řešení a projekty. **/Maxcpucount:**_číslo_ (nebo **/m:**_číslo_) možnost příkazového řádku pro nástroj MSBuild.exe můžete vytvořit více projektů stejnou dobu. A **/MP** – možnost kompilátoru můžete vytvořit více kompilačních jednotek ve stejnou dobu. Pokud jsou vhodné pro vaše aplikace, zrychlit uvádění sestavení vašeho řešení pomocí jedné nebo obou **/MP** a **/maxcpucount**.

Čas sestavení vašeho řešení závisí částečně na počet procesů, které provádějí sestavení. *Číslo* argument [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild určuje maximální počet projektů k sestavení ve stejnou dobu. Podobně *processMax* argument **/MP** – možnost kompilátoru určuje maximální počet jednotek kompilace na sestavení ve stejnou dobu. Pokud **/maxcpucount** určuje možnost *P* projekty a **/MP** určuje možnost *C* zpracovává, nesmí být delší *P*  x *C* procesy spuštění ve stejnou dobu.

Pokyny pro rozhodování o tom, jestli se má použít nástroj MSBuild nebo **/MP** technologie vypadá takto:

- Pokud existuje mnoho projektů s několika souborů v každém projektu, použijte nástroj MSBuild.

- Pokud je k několika projektů s velkým množstvím souborů v každém projektu, **/MP** možnost.

- Pokud se rovnováha počet projektů a souborů na projektu, použijte MSBuild a **/MP**. Na začátku nastavit **/maxcpucount** možnost počet projektů k sestavení a **/MP** možnost počet procesorů v počítači. Měření výkonu a pak upravte nastavení výnosu z nejlepších výsledků. Opakujte tento cyklus, dokud nebudete s časem celkový počet sestavení.

#### <a name="the-gm-compiler-option"></a>/Gm – možnost kompilátoru

Ve výchozím nastavení, sestavení projektu umožňuje **/Gm** – možnost kompilátoru (přírůstková sestavení) pro sestavení pro ladění a zakáže ho pro verzi sestavení. Proto **/MP** – možnost kompilátoru je automaticky zakázáno v sestavení ladění, protože je v konfliktu s výchozí **/Gm** – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[#import – direktiva](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Referenční dokumentace k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf (rychlejší generování souborů PDB)](zf.md)<br/>
