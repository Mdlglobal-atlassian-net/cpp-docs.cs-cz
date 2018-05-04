---
title: -SWAPRUN (Načíst výstup Linkeru do souboru odkládacího souboru) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs:
- C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 522cd693da1b4e1a72d11119f622d862413b409b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Načíst výstup linkeru do souboru odkládacího souboru)
```  
/SWAPRUN:{NET|CD}  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /SWAPRUN informuje linkeru výstup do souboru odkládacího souboru a pak spusťte bitovou kopii z operačního systému do prvního kopírování. Toto je funkce systému Windows NT 4.0 (nebo novější).  
  
 Pokud je zadán NET, operační systém nejprve zkopírovat binární image ze sítě do odkládacího souboru a načíst z ní. Tato možnost je užitečná pro spouštění aplikací přes síť. Pokud je zadána disku CD-ROM, bude operační systém zkopírovat bitovou kopii na vyměnitelném disku do souboru stránky a pak můžete načíst.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **systému** stránku vlastností.  
  
4.  Upravte jednu z následujících vlastností:  
  
    -   **Swap spustit z disku CD-ROM.**  
  
    -   **Swap – spuštění ze sítě**  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)