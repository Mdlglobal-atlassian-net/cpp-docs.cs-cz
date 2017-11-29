---
title: "-X (ignorování standardních cest zahrnutí) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
dev_langs: C++
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ed251e1b937d14c42d105d98c2771ed0a2d6172
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="x-ignore-standard-include-paths"></a>/X (ignorování standardních cest zahrnutí)
Zabrání kompilátoru hledání zahrnout soubory v adresářích zadaný v proměnné prostředí PATH a zahrnout.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/X  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít tuto možnost se [/I (Další adresáře Include)](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) možnost.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **preprocesor** stránku vlastností.  
  
4.  Změnit **Ignorovat standardní cestu zahrnují** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkazu `/X` říká kompilátoru ignorovat umístění zadaná pomocí proměnné prostředí PATH a zahrnout, a `/I` Určuje adresář, ve kterém má být vyhledán zahrnout soubory:  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)