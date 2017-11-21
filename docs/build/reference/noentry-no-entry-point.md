---
title: "-NOENTRY (bez vstupního bodu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
dev_langs: C++
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8d3e44f3181683a7a0c2c7725e2a6567895fdd0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (bez vstupního bodu)
```  
/NOENTRY  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /NOENTRY je vyžadována pro vytváření pouze knihovny DLL, která neobsahuje žádný spustitelný kód. Další informace najdete v tématu [vytváření knihovny DLL Resource-Only](../../build/creating-a-resource-only-dll.md).  
  
 Tuto možnost použijte, chcete-li zabránit nástroji LINK v propojení odkazu na metodu `_main` do knihovny DLL.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **Upřesnit** stránku vlastností.  
  
4.  Změnit **žádný vstupní bod** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření knihovny DLL určené pouze](../../build/creating-a-resource-only-dll.md)   
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)