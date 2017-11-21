---
title: "-LARGEADDRESSAWARE (zpracování velkých adres) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs: C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 033e93b3f1f6457a1283a14371a3f7619fe60792
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (zpracování velkých adres)
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/LARGEADDRESSAWARE informuje linkeru, zda aplikace dokáže zvládat adresy větší než 2 GB. V 64bitových kompilátory je tato možnost povolená ve výchozím nastavení. V kompilátory 32-bit /LARGEADDRESSAWARE:NO je povoleno, pokud není uvedeno jinak/LARGEADDRESSAWARE na řádku linkeru.  
  
 Pokud aplikace bylo propojeno s/LARGEADDRESSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) se zobrazí informace o tom.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **systému** stránku vlastností.  
  
4.  Změnit **povolit velkých adres** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)