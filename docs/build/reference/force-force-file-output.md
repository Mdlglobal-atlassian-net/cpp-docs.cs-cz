---
title: -FORCE (vynutit výstup souboru) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1daa27ce48590d4a122eafde9f63f7142271610
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="force-force-file-output"></a>/FORCE (Vynutit výstup souboru)
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/Force informuje linkeru pro vytvoření souboru platný .exe nebo knihovny DLL i v případě, že symbol odkazuje ale není definované nebo je násobení definované.  
  
 Možnost/Force může trvat nepovinný argument:  
  
-   /FORCE:MULTIPLE použijte k vytvoření výstupního souboru, zda odkaz zjistí víc než jednu definici pro symbol.  
  
-   Použít/Force: NEVYŘEŠENA, aby vytvoření výstupního souboru, zda odkaz vyhledá nedefinované symbol. / FORCE: NEROZPOZNANÉ je ignorována, pokud je symbol vstupní bod nebyl vyřešen.  
  
 / FORCE bez argumentů znamená i více a nevyřešena.  
  
 Soubor vytvořený pomocí této možnosti nebude fungovat podle očekávání. Linkeru nebude přírůstkově propojit – Pokud je zadána možnost/Force.  
  
 Pokud je modul kompilován s **/CLR**, **/FORCE** nevytvoří bitovou kopii.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)