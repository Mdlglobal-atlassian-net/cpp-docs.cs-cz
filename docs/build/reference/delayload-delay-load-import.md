---
title: "-DELAYLOAD (Import odloženého načtení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs: C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fd524e72125408c6a88bea83272e18a7ef9b78d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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