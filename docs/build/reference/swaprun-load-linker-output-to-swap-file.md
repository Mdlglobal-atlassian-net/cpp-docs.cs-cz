---
title: "-SWAPRUN (Načíst výstup Linkeru do souboru odkládacího souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3b6829a20e80ab8548460205169e1cd258694e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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