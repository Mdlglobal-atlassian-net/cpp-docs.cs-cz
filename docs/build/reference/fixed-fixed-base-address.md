---
title: -FIXED (pevná základní adresa) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1193b7cfe58aed45e4feec598a49227eafc87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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