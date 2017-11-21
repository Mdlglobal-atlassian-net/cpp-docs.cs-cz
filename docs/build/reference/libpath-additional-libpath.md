---
title: "-LIBPATH (další proměnná Libpath) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs: C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2bef6a2294bab34cf9dfc59e352e1b79376b146
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (další proměnná Libpath)
```  
/LIBPATH:dir  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `dir`  
 Určuje cestu, bude před vyhledávání cesta zadaný v možnosti prostředí LIB hledání linkeru.  
  
## <a name="remarks"></a>Poznámky  
 / Libpath možnost slouží k přepisu danou cestu knihovny prostředí. Linkeru se nejprve vyhledat v cestu určenou položkou tuto možnost a pak vyhledejte cestu zadanou v proměnná prostředí LIB. Můžete zadat pouze jeden adresář pro každý/Libpath – možnost, které zadáte. Pokud chcete zadat více než jeden adresář, zadejte více možnosti/Libpath. Linkeru prohledá zadaných adresářích v pořadí.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Obecné** stránku vlastností.  
  
4.  Změnit **další adresáře knihovny** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)