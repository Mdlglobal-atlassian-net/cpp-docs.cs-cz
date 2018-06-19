---
title: -LIBPATH (další proměnná Libpath) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ccb94ad20735e81fc3d83f757cc0265cdc32169
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372877"
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