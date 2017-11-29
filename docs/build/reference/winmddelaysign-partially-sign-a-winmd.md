---
title: "-WINMDDELAYSIGN (částečné podepsání souboru winmd) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs: C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18f168c9a3faf4a6bc2676e142a35ee6314db391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (Částečné podepsání souboru winmd)
Umožňuje částečné podepsání souboru metadat Windows Runtime (.winmd) umístěním veřejný klíč v souboru.  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Vypadá takto: [/delaysign](../../build/reference/delaysign-partially-sign-an-assembly.md) propojovacího, který se použije k souboru .winmd. Použití **/WINMDDELAYSIGN** Pokud chcete do souboru .winmd umístit pouze veřejný klíč. Ve výchozím nastavení, linkeru funguje jako **/WINMDDELAYSIGN:NO** byly zadány; to znamená, že ho není podepsání souboru winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **metadat Windows** stránku vlastností.  
  
4.  V **Windows Metadata odložené podepisování** rozevíracího seznamu vyberte požadovanou možnost.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)