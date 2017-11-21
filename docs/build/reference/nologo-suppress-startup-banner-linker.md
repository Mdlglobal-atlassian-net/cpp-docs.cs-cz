---
title: "-NOLOGO (Potlačit úvodní nápis při spouštění) (Linker) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs: C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1460563303f6a619d316a1b3ff4f885a31247a72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Potlačit úvodní nápis při spouštění) (linker)
```  
/NOLOGO  
```  
  
## <a name="remarks"></a>Poznámky  
 / Nologo možnost zabraňuje zobrazení číslo autorským zprávu a verze.  
  
 Tato možnost také potlačí zobrazení příkazové soubory. Podrobnosti najdete v tématu [soubory příkazů LINK](../../build/reference/link-command-files.md).  
  
 Ve výchozím nastavení tyto informace se odesílají podle linkeru do okna výstupu. Na příkazovém řádku je odeslána do standardního výstupního a můžete přesměrovat do souboru.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Tuto možnost lze používat pouze z příkazového řádku.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  Tato možnost linkeru nelze změnit prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)