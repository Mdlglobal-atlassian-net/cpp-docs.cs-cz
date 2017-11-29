---
title: "-WINMDKEYCONTAINER (určení kontejneru klíče) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.WINMDKEYCONTAINER
dev_langs: C++
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a7fc567d9b9f4a70c42effec80595b0d33c0cad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (Určení kontejneru klíče)
Určuje kontejner klíčů pro podepsání souboru metadat Windows (.winmd).  
  
```  
/WINMDKEYCONTAINER:name  
```  
  
## <a name="remarks"></a>Poznámky  
 Vypadá takto: [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) – možnost linkeru použitý na soubor (.winmd).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **metadat Windows** stránku vlastností.  
  
4.  V **kontejneru klíčů metadat Windows** zadejte umístění.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)