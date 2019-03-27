---
title: Možnosti BSCMAKE
ms.date: 11/04/2016
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
ms.openlocfilehash: b1d62e8d122cb4f08feef60d6936359b3e246749
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508777"
---
# <a name="bscmake-options"></a>Možnosti BSCMAKE

> [!WARNING]
> Přestože BSCMAKE je stále instalace sady Visual Studio, se už používá integrovaným vývojovým prostředím. Od verze Visual Studio 2008 je automaticky uloženy informace o procházení a symbol v soubor SDF SQL serveru ve složce řešení.

Tato část popisuje dostupné možnosti pro řízení BSCMAKE. Několik možností, jak obsah informačního souboru procházení řízen vyloučení nebo zahrnutí určité informace. Možnosti vyloučení můžete povolit BSCMAKE běželo rychleji a může mít za následek menší soubor .bsc. Názvy možností jsou malá a velká písmena (s výjimkou **/HELP** a **/nologo**).

Pouze **/nologo** a **/o** jsou dostupné v rámci vývojového prostředí sady Visual Studio.  Zobrazit [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md) o přístup k stránky vlastností projektu.

**/Ei (** *filename*... **)**<br/>
Obsah souboru určeného zahrnutého vyloučí z informačního souboru procházení. Chcete-li zadat více souborů, názvy oddělte mezerou a uvést v seznamu v závorkách. Závorky nejsou nezbytné, pokud zadáte pouze jeden *filename*. Použití **/Ei** spolu s **/Es** možnost vyloučit soubory není vyloučeno podle **/Es**.

**/El**<br/>
Vyloučí místní symboly. Ve výchozím nastavení je místní symboly. Další informace o místní symboly, naleznete v tématu [vytváření souboru .sbr](creating-an-dot-sbr-file.md).

**/Em**<br/>
Vyloučí symboly v těle makra. Použití **/Em** mají být zahrnuty pouze názvy maker informačního souboru procházení. Ve výchozím nastavení je zahrnout názvy maker a výsledkem rozšíření makra.

**/ER (** *symbol*... **)**<br/>
Vyloučí zadaný symboly z informačního souboru procházení. Chcete-li zadat více názvů symbol, názvy oddělte mezerou a uvést v seznamu v závorkách. Závorky nejsou nezbytné, pokud zadáte pouze jeden *symbol*.

**/Es**<br/>
Vyloučí z informačního souboru procházení každý soubor zahrnutí zadán s parametrem absolutní cestu nebo absolutní cesta zadaná v proměnné prostředí INCLUDE součástí. (Obvykle se jedná o systému vkládané soubory, které obsahují velké množství informací, které nemusí být nutné v informačního souboru procházení.) Tato možnost nevylučuje zadaných bez cesty, nebo relativní cesty nebo soubory nalezené v relativní cestu VLOŽENÝCH souborů. Můžete použít **/Ei** možnost spolu s **/Es** vyloučit soubory, které **/Es** nevylučuje. Pokud budete chtít vyloučit pouze některé soubory, které **/Es** vyloučí, použijte **/Ei** místo **/Es** a seznam souborů, které chcete vyloučit.

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
Umožňuje odesílat informace společnosti Microsoft týkající se s interními chybami v bscmake.exe.

Další informace o **/errorreport**, naleznete v tématu [/errorreport (sestava interními chybami kompilátoru)](errorreport-report-internal-compiler-errors.md).

**/HELP**<br/>
Zobrazí souhrn syntaxe příkazového řádku nástroje BSCMAKE.

**/Iu**<br/>
Zahrnuje neodkazovaná symboly. Ve výchozím nastavení BSCMAKE nezaznamenává všechny symboly, které jsou definovány, ale neodkazuje. Pokud soubor .sbr byla zabalena, tato možnost nemá žádný účinek pro tento vstupní soubor, protože kompilátor už odebrala neodkazovaná symboly.

**/n**<br/>
Vynutí nepřírůstková sestavení. Použití **/n** vynutit na úplné sestavení informačního souboru procházení, jestli existuje soubor .bsc a zabránit soubory .sbr vedlo ke zkrácení. Zobrazit [postupy: sestavení souboru .BSC nástrojem BSCMAKE](how-bscmake-builds-a-dot-bsc-file.md).

**/NOLOGO**<br/>
Potlačí zprávu o autorských právech nástroje BSCMAKE.

**/o** *název souboru*<br/>
Určuje název informačního souboru procházení. Ve výchozím nastavení BSCMAKE poskytuje informačního souboru procházení základní název prvního souboru .sbr a rozšíření .bsc.

**/S (** *filename*... **)**<br/>
Říká BSCMAKE zpracovat určeného zahrnutého souboru okamžiku, kdy byla zjištěna a vyloučit jinak. Tuto možnost použijte, chcete-li ušetřit čas zpracovávání, když je součástí několika zdrojových souborů soubor (například záhlaví, nebo .h, souboru .c nebo .cpp zdrojový soubor), ale je beze změny pomocí direktivy předběžného zpracování pokaždé, když. Můžete také chtít tuto možnost použijte, pokud se soubor změní způsoby, které nejsou důležité pro informačního souboru procházení, kterou vytváříte. Chcete-li zadat více souborů, názvy oddělte mezerou a uvést v seznamu v závorkách. Závorky nejsou nezbytné, pokud zadáte pouze jeden *filename*. Pokud budete chtít vyloučit souboru pokaždé, když je součástí, použít **/Ei** nebo **/Es** možnost.

**/v**<br/>
Poskytuje podrobný výstup, který obsahuje název každého souboru .sbr zpracovává a informace o dokončení BSCMAKE spustit.

**/?**<br/>
Obsahuje stručný přehled syntaxe příkazového řádku nástroje BSCMAKE.

Následující příkazový řádek říká BSCMAKE provést úplné sestavení MAIN.bsc ze tří soubory .sbr. Také poskytuje nástroje BSCMAKE vyloučit duplicitní instance TOOLBOX.h:

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>Viz také:

[BSCMAKE – referenční dokumentace](bscmake-reference.md)
