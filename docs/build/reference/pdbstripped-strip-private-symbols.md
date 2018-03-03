---
title: "-PDBSTRIPPED (Odstranit privátní symboly) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs:
- C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff124dec52a77ed5bf35d2454f95854ebea5eea0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Odstranit privátní symboly)
```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *pdb_file_name*  
 Název zadaného uživatelem pro databázi odřapíkovaného programu (PDB), který vytváří linkeru.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /PDBSTRIPPED vytvoří druhý soubor databáze (PDB), programu při vytvoření bitové kopie programu s žádným z kompilátoru nebo linkeru možnosti, které generují soubor PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), /Zd nebo /Zi). Tento druhý soubor PDB vynechá znaky, které byste neměli chtít dodávat zákazníkům. Druhý soubor PDB bude obsahovat pouze:  
  
-   Veřejné symboly  
  
-   Seznam souborů objekt a části spustitelný soubor, ke kterému přispívají  
  
-   Rámce ukazatel optimalizace (FPO) ladění záznamy používá k procházení zásobníku  
  
 Odřapíkovaného soubor PDB nebude obsahovat:  
  
-   Informace o typu  
  
-   Informace o čísle řádku  
  
-   Na objekt souboru CodeView symboly jsou pro funkce, místní a statických dat  
  
 Celého souboru PDB přesto vygeneruje, když používáte /PDBSTRIPPED.  
  
 Pokud nevytvoříte soubor PDB, /PDBSTRIPPED ignorována.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **ladění** stránku vlastností.  
  
4.  Změnit **Odstranit privátní symboly** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)