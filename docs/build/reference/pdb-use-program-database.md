---
title: -PDB (použít databázi programu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs:
- C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 776d23c0c0c7ce392b1ff0d7a989c3c5503129b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pdb-use-program-database"></a>/PDB (Použít databázi programu)
```  
/PDB:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Název zadaného uživatelem pro databázi programu (PDB), který vytváří linkeru. Nahradí výchozí název.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení když [/DEBUG](../../build/reference/debug-generate-debug-info.md) není zadaný, linkeru vytvoří databázi programu (PDB), která obsahuje informace o ladění. Výchozí název souboru PDB má základní název programu a PDB rozšíření.  
  
 Použít/pdb:*filename* k zadání názvu souboru PDB. Pokud není zadán/Debug, možnost/PDB je ignorována.  
  
 Soubor PDB může být až 2GB.  
  
 Další informace najdete v tématu [soubory .pdb jako vstup Linkeru](../../build/reference/dot-pdb-files-as-linker-input.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **ladění** stránku vlastností.  
  
4.  Změnit **generování souboru databáze programu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)