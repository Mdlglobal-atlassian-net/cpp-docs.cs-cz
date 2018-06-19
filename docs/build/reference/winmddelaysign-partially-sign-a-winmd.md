---
title: -WINMDDELAYSIGN (částečné podepsání souboru winmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c50480fae1f4f3e7421236615d059a642d1074f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375555"
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