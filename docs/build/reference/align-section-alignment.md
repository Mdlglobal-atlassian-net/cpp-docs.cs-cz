---
title: "-ALIGN (zarovnání oddílů) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs: C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e620719d5a69c333a45664fba5967a740224d4d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="align-section-alignment"></a>/ALIGN (zarovnání oddílů)
```  
/ALIGN[:number]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `number`  
 Zarovnání hodnota.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /ALIGN Určuje zarovnání každého oddílu v lineární adresní prostor programu. `number` Argument je v bajtech a musí být násobek dvou. Výchozí hodnota je 4K (4096). Linkeru vydá upozornění, pokud zarovnání vytvoří bitovou kopii neplatný.  
  
 Pokud píšete aplikace například ovladač zařízení, by neměl muset upravit zarovnání.  
  
 Je možné upravit zarovnání s parametrem align do určitého oddílu [/SECTION](../../build/reference/section-specify-section-attributes.md) možnost.  
  
 Zarovnání hodnotu, která zadáte nemůže být menší než největší zarovnání oddílů.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)