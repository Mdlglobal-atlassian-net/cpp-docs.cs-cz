---
title: -Fo (název souboru objektů) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea552b149270b8e644140a4dd51f220648ef376e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fo-object-file-name"></a>/Fo (název souboru objektů)
Určuje název objektu (.obj) soubor nebo adresář, který se má použít místo výchozí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fopathname  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete tuto možnost, soubor objektu používá základní název zdrojového souboru a .obj rozšíření. Můžete použít libovolný název a příponu má ale doporučené konvence, je použít. objektu vývoz.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **výstupní soubory** stránku vlastností.  
  
4.  Změnit **název souboru objektů** vlastnost.  Ve vývojovém prostředí, musí mít objekt souboru rozšíření. objektu vývoz.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří soubor objektu s názvem THIS.obj v existující adresář, \OBJECT, na jednotce B.  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)