---
title: "-FORCE (vynutit výstup souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs: C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2990ff88e896c7cafb3ff8eb2d9acf149d7a90c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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