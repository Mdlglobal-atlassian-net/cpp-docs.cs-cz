---
title: -WINMDFILE (určení souboru winmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eaf1bfc805db568a012c28d66361bbd99745a95
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375594"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (Určení souboru winmd)
Určuje název souboru pro výstupní soubor metadat Windows Runtime (.winmd), který je generovaný [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) – možnost linkeru.  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 Použít hodnotu, která je zadána v `filename` přepsat výchozí název souboru .winmd (`binaryname`.winmd). Všimněte si ".winmd" nepřidáte do `filename`.  Pokud více hodnot, které jsou uvedené na **/WINMDFILE** příkazového řádku, jako poslední má přednost před.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **metadat Windows** stránku vlastností.  
  
4.  V **soubor metadat Windows** zadejte umístění souboru.  
  
## <a name="see-also"></a>Viz také  
 [/ WINMD (generování metadat Windows)](../../build/reference/winmd-generate-windows-metadata.md)   
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)