---
title: Možnosti BSCMAKE
description: Odkaz na možnosti příkazového řádku nástroje Microsoft BSCMAKE
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257790"
---
# <a name="bscmake-options"></a>Možnosti BSCMAKE

> [!WARNING]
> I když je aplikace BSCMAKE stále nainstalována se sadou Visual Studio, již není používána rozhraním IDE. Vzhledem k tomu, že se Visual Studio 2008, informace o procházení a symbolech se ukládají automaticky do souboru SQL Server *`.sdf`* ve složce řešení.

Tato část popisuje možnosti, které jsou k dispozici pro řízení BSCMAKE. Několik možností řídí obsah souboru s informacemi o procházení a vylučuje nebo obsahuje určité informace. Možnosti vyloučení můžou BSCMAKE běžet rychleji a může mít za následek menší *`.bsc`* soubor. V názvech možností se rozlišují velká a malá písmena (s výjimkou **/help** a **/nologo**).

V rámci vývojového prostředí sady Visual Studio jsou k dispozici pouze prostředí **/nologo** a **/o** .  Informace o přístupu na stránky vlastností projektu naleznete v tématu [Nastavení vlastností kompilátoru a sestavení v C++ sadě Visual Studio](../working-with-project-properties.md) .

**/EI (** _název souboru_... **)** \
Vyloučí obsah zadaných souborů include ze souboru informací o procházení. Chcete-li zadat více souborů, oddělte názvy mezerami a seznam uveďte v závorkách. Závorky nejsou nutné, pokud zadáte pouze jeden *název souboru*. Použijte **/EI** spolu s možností **/ES** k vyloučení souborů, které nevylučuje **/ES**.

**/El**\
Vyloučí místní symboly. Výchozím nastavením je zahrnutí místních symbolů. Další informace o místních symbolech naleznete v tématu [Vytvoření souboru. sbr](creating-an-dot-sbr-file.md).

**/Em**\
Vyloučí symboly v textu maker. Použijte **/em** k zahrnutí pouze názvů maker do souboru s informacemi o procházení. Výchozím nastavením je zahrnutí názvů maker a výsledku rozšíření makra.

**/ER (** _symbol_... **)** \
Vyloučí zadané symboly ze souboru s informacemi o procházení. Chcete-li zadat více názvů symbolů, oddělte názvy mezerami a seznam uveďte v závorkách. Pokud zadáte jenom jeden *symbol*, nepotřebujete závorky.

**/Es**\
Vyloučí všechny vložené soubory s absolutní cestou, nebo se nachází v absolutní cestě zadané v proměnné prostředí INCLUDE. (Obvykle se jedná o systémové soubory k zahrnutí, které obsahují mnoho informací, které nemusí být v souboru s informacemi o procházení potřeba.) Tato možnost nevylučuje soubory zadané bez cesty, nebo s relativními cestami, nebo soubory nalezené v relativní cestě v příkazu INCLUDE. Můžete použít možnost **/EI** spolu s **/ES** k vyloučení souborů, které **/ES** nevylučuje. Chcete-li vyloučit pouze některé soubory, použijte **/EI** namísto **/ES**a seznam souborů, které chcete vyloučit.

**/errorreport:** [**žádné** &#124; &#124; &#124; **odeslání**fronty výzvy] \
Tato možnost je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

**/Help**\
Zobrazí souhrn syntaxe příkazového řádku BSCMAKE.

**/Iu**\
Obsahuje neodkazované symboly. Ve výchozím nastavení BSCMAKE nezaznamenává žádné symboly, které jsou definovány, ale nejsou odkazovány. Pokud byl soubor *`.sbr`* zabalen, nemá tato možnost žádný vliv na tento vstupní soubor, protože kompilátor již odebral neodkazované symboly.

**/n**\
Vynutí nepřírůstkové sestavení. Pomocí **/n** vynutíte úplné sestavení souboru s informacemi o procházení, ať už *`.bsc`* soubor existuje, nebo ne, a zabráníte tak zkrácení *`.sbr`* souborů. Podívejte [se, jak BSCMAKE vytváří soubor. BSC](how-bscmake-builds-a-dot-bsc-file.md).

**/Nologo** –\
Potlačí zprávu o autorských právech BSCMAKE.

**/o** *název_souboru*\
Určuje název souboru s informacemi o procházení. Ve výchozím nastavení poskytuje BSCMAKE soubor s informacemi o procházení jako základní název prvního *`.sbr`* souboru a přípona *`.bsc`* .

**/S (** _název souboru_... **)** \
Oznamuje BSCMAKE zpracování zadaného souboru include při prvním výskytu a jeho vyloučení v opačném případě. Tato možnost slouží k uložení doby zpracování, když je soubor (například hlavička nebo *`.h`* , soubor pro *`.c`* nebo *`.cpp`* zdrojového souboru) zahrnut do několika zdrojových souborů, ale nemění se pokaždé, když se používají direktivy předzpracování. Tuto možnost použijte, pokud se změní soubor způsobem, který je neimportovaná pro soubor informací o procházení, který vytváříte. Chcete-li zadat více souborů, oddělte názvy mezerami a seznam uveďte v závorkách. Závorky nejsou nutné, pokud zadáte pouze jeden *název souboru*. Pokud chcete soubor vyloučit pokaždé, když je zahrnutý, použijte možnost **/EI** nebo **/ES** .

**/v**\
Poskytuje podrobný výstup, který zahrnuje název každého zpracovávaného souboru *`.sbr`* a informace o dokončeném spuštění BSCMAKE.

**/?** \
Zobrazí stručný souhrn syntaxe příkazového řádku BSCMAKE.

Následující příkazový řádek oznamuje BSCMAKE úplné sestavení MAIN. BSC ze tří souborů *`.sbr`* . Také udává, že BSCMAKE vyloučí duplicitní instance sady nástrojů. h:

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Viz také

[BSCMAKE – referenční dokumentace](bscmake-reference.md)
