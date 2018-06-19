---
title: -NOLOGO (Potlačit úvodní nápis při spouštění) (Linker) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76e99496114c0ebdc60f81724e67dd88a482055
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374190"
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