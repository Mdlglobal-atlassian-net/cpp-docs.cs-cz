---
title: Možnosti BSCMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- C++
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46c258a5591615bb277823ccc5261fade3c5e2af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-options"></a>Možnosti BSCMAKE
Tato část popisuje možnosti dostupné pro řízení BSCMAKE. Několik možností obsah soubor s informacemi o procházení řídit vyloučení nebo zahrnutí určité informace. Možnosti vyloučení můžete povolit BSCMAKE spouštět rychleji a může mít za následek menší souboru BSC programem. Možnost názvů malá a velká písmena (s výjimkou **/HELP** a **/nologo**).  
  
 Pouze **/nologo** a **/o** jsou k dispozici ve vývojovém prostředí sady Visual Studio.  V tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md) informace o přístup k stránky vlastností projektu.  
  
 /Ei ( `filename`...)  
 Obsah zadaného zahrnout soubory vyloučí z soubor s informacemi o procházení. Chcete-li zadat více souborů, názvy oddělte mezerou a seznam uvést v závorkách. Závorky nejsou nutné v případě, že zadáváte pouze jednu `filename`. Použití **/Ei** spolu s **/Es** možnost vyloučit soubory není vyloučený **/Es**.  
  
 /El  
 Vyloučí lokální symboly. Ve výchozím nastavení se místní symboly. Další informace o lokální symboly najdete v tématu [vytváření souboru .sbr](../../build/reference/creating-an-dot-sbr-file.md).  
  
 /Em  
 Vyloučí symboly v těle makra. Použití **/Em** mají být zahrnuty pouze názvy makra soubor s informacemi o procházení. Výchozí hodnota je makro názvy a výsledek makro rozšíření.  
  
 /ER ( `symbol`...)  
 Zadané symboly vyloučí z soubor s informacemi o procházení. Chcete-li zadat více názvů symbol, názvy oddělte mezerou a seznam uvést v závorkách. Závorky nejsou nutné v případě, že zadáváte pouze jednu `symbol`.  
  
 /ES  
 Vyloučí z soubor s informacemi o procházení každý soubor zahrnout zadaným absolutní cestu nebo byla nalezena v určeném v proměnné prostředí zahrnout absolutní cesta. (Obvykle, jedná se o systému obsahovat soubory, které obsahují mnoho informace, které nemusí být nutné v váš soubor s informacemi o procházení.) Tato možnost není vyloučit soubory zadané bez cesty, nebo relativní cesty nebo soubory, které jsou relativní cestu v zahrnout. Můžete použít **/Ei** možnost spolu s **/Es** vyloučit soubory, které **/Es** není vyloučit. Pokud chcete vyloučit jenom některé soubory, **/Es** vyloučí, použijte **/Ei** místo **/Es** a seznam souborů, které chcete vyloučit.  
  
 / errorreport: [žádné &#124; řádku &#124; fronty &#124; odeslat]  
 Umožňuje odesílat informace společnosti Microsoft týkající se vnitřní chyby v bscmake.exe.  
  
 Další informace o **/errorreport**, najdete v části [/errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 / HELP  
 Zobrazí souhrn syntaxe příkazového řádku BSCMAKE.  
  
 /IU  
 Zahrnuje neregistrované symboly. Ve výchozím nastavení BSCMAKE nezaznamenává všechny symboly, které jsou definovány, ale neodkazuje. Pokud soubor .sbr byly zabaleny, tato možnost nemá žádný vliv pro tento vstupní soubor, protože kompilátor již odebrána neregistrované symboly.  
  
 /n  
 Vynutí nonincremental sestavení. Použití  **/n**  Chcete-li vynutit úplnou sestavení informačního souboru procházet, jestli existuje soubor .bsc a zabránit ke zkrácení .sbr souborů. V tématu [jak BSCMAKE sestavení souboru BSC programem](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md).  
  
 /NOLOGO  
 Potlačí zprávu o autorských právech BSCMAKE.  
  
 /o`filename`  
 Určuje název pro soubor s informacemi o procházení. Ve výchozím nastavení BSCMAKE poskytuje soubor s informacemi o procházení základní název první soubor .sbr a .bsc rozšíření.  
  
 /S ( `filename`...)  
 Informuje BSCMAKE zpracovat zadaný soubor poprvé, kdy je zjištěn a chcete vyloučit jinak. Tuto možnost použijte, chcete-li ušetřit čas zpracování při souboru (například záhlaví, nebo .h, souboru .c nebo zdrojového souboru) je součástí několika zdrojové soubory, ale je beze změny pomocí direktivy předběžného zpracování pokaždé, když. Můžete také tuto možnost použijte, pokud dojde ke změně souboru způsobem, který je důležitý pro soubor s informacemi o procházení, kterou vytváříte. Chcete-li zadat více souborů, názvy oddělte mezerou a seznam uvést v závorkách. Závorky nejsou nutné v případě, že zadáváte pouze jednu `filename`. Pokud chcete vyloučit souboru pokaždé, když je zahrnuta, použijte **/Ei** nebo **/Es** možnost.  
  
 /v  
 Poskytuje podrobný výstup, který obsahuje název každého souboru .sbr zpracovávána a informace o dokončení BSCMAKE spustit.  
  
 /?  
 Zobrazuje stručné souhrnné informace o BSCMAKE syntaxe příkazového řádku.  
  
 Následující příkazový řádek říká BSCMAKE lze dosáhnout úplné sestavení MAIN.bsc z tři soubory .sbr. Poskytuje také BSCMAKE vyloučit duplicitní instance TOOLBOX.h:  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## <a name="see-also"></a>Viz také  
 [BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)