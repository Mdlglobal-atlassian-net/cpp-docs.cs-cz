---
title: "-FIXED (pevná základní adresa) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 201a0357d182713c473fd3e259e4e9c2a71abf4e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Pevná základní adresa)
```  
/FIXED[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Informuje načíst pouze při jeho upřednostňovaná základní adresa programu operačního systému. Pokud není k dispozici upřednostňovaná základní adresa, operačního systému nepodaří načíst soubor. Další informace najdete v tématu [/BASE (základní adresa)](../../build/reference/base-base-address.md).  
  
 /FIXED:NO je výchozí nastavení pro knihovny DLL a /FIXED je výchozí nastavení pro jakýkoli jiný typ projektu.  
  
 Pokud je zadána /FIXED, odkaz negeneruje přemístění oddíl v programu. V době běhu Pokud operačního systému se nepodařilo načíst programu na zadané adrese ji vystavuje chybovou zprávu a nenačte program.  
  
 Zadejte /FIXED:NO ke generování přemístění oddíl v programu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte název možnosti a nastavení v **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)