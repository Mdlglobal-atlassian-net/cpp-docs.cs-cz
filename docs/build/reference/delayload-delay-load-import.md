---
title: -DELAYLOAD (Import odloženého načtení) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74d65caa8a0ea140f93bf156e3c14a85232e6e56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (import odloženého načtení)
```  
/DELAYLOAD:dllname  
```  
  
## <a name="parameters"></a>Parametry  
 `dllname`  
 Název knihovny DLL, kterou chcete zpoždění zatížení.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /DELAYLOAD způsobí, že knihovnu DLL, která je zadána `dllname` načíst pouze při prvním volání programem tak, aby funkce v této knihovně DLL. Další informace najdete v tématu [podpora Linkeru pro knihovny DLL Delay-Loaded](../../build/reference/linker-support-for-delay-loaded-dlls.md). Tuto možnost můžete podle potřeby několikrát k určení tolik knihovny DLL a zvolte. Při propojení vašeho programu nebo můžete implementovat vlastní pomocné funkce zpoždění zatížení, je nutné použít Delayimp.lib.  
  
 [/DELAY](../../build/reference/delay-delay-load-import-settings.md) možnost určuje vazby a načítání možnosti pro každou knihovnu DLL načtené se zpožděním.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V **Linkeru** složky, vyberte **vstup** stránku vlastností.  
  
3.  Změnit **DLL s odloženým načtením** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)