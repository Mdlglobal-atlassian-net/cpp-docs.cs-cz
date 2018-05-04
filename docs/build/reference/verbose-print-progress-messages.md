---
title: -VERBOSE (Tisk zpráv průběhu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
dev_langs:
- C++
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee1bf99cdf27e432bf8bdf6b7c0e48a84aeaac21
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (tisk zpráv průběhu)
```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## <a name="remarks"></a>Poznámky  
 Linkeru odesílá informace o průběhu vytváření relace k **výstup** okno. Na příkazovém řádku informace odeslán do standardního výstupního a můžete přesměrovat do souboru.  
  
|Možnost|Popis|  
|------------|-----------------|  
|/ VERBOSE|Zobrazí podrobnosti o proces propojení.|  
|/ VERBOSE: BRÁNOU FIREWALL|Zobrazení informací o linkeru aktivity, která je výsledkem použití [/OPT:ICF](../../build/reference/opt-optimizations.md).|  
|/ VERBOSE: INCR|Zobrazí informace o procesu přírůstkové odkaz.|  
|/ VERBOSE: LIB|Zobrazí průběh zprávy, které uvádět jenom knihovny vyhledávat.<br /><br /> Zobrazené informace zahrnují proces vyhledávání knihovny a uvádí každý název knihovny a objektu (s úplnou cestou), symbol překládán z knihovny a seznam objektů, které odkazují na symbol.|  
|/ VERBOSE: REF|Zobrazí informace o linkeru aktivity, která je výsledkem použití [/OPT:REF](../../build/reference/opt-optimizations.md).|  
|/ VERBOSE: SAFESEH|Zobrazí informace o moduly, které nejsou kompatibilní s bezpečné při zpracování výjimek [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) není zadán.|  
|/ VERBOSE: UNUSEDLIBS|Zobrazí informace o souborech žádné knihovny, které nejsou používány, když se vytvoří bitovou kopii.|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **Linkeru** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Možnost Přidat **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)