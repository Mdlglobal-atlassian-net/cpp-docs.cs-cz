---
title: -FI (název musí obsahovat soubor) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
- /fi
dev_langs:
- C++
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b85bfaebe09203f7aad76c24e8f8fbccfe009d80
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fi-name-forced-include-file"></a>/FI (Zahrnutý soubor s povinným názvem)
Způsobí, že preprocesor při zpracování souboru zadaná hlavička.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FI[ ]pathname  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost je výsledek stejný jako zadání dvojitých uvozovek nahoře v souboru `#include` direktivy na první řádek každý zdrojový soubor, který je zadán v příkazovém řádku, do proměnné prostředí CL nebo soubor příkazů. Pokud používáte více **/FI** možnosti, soubory jsou zahrnuty v pořadí, jsou zpracovávány CL.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **obsahuje vynucené** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)