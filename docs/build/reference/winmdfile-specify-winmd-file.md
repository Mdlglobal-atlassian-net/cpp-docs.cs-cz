---
title: "-WINMDFILE (určení souboru winmd) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs: C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a503ef23b6aa1c42bb4b480de7879d2392825869
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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