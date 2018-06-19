---
title: -showIncludes (seznam obsahovat soubory) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eac7df694994b625e08ded710d43837d857df2d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378337"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (seznam vložených souborů)
Způsobí, že kompilátor výstup seznam zahrnout soubory. Vnořené zahrnout soubory jsou také zobrazených (soubory, které jsou zahrnuty ze souborů, které zahrnete).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/showIncludes  
```  
  
## <a name="remarks"></a>Poznámky  
 Vložené soubory je došlo během kompilace, zprávu při výstup, například:  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 Vnořené zahrnout soubory jsou označeny odsazení jediného místa pro každou úroveň vnoření, například:  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 V takovém případě `2.h` byl součástí z `1.h`, proto odsazení.  
  
 **/Showincludes vložených** možnost vysílá k `stderr`, nikoli `stdout`.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **zobrazit zahrnuje** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)