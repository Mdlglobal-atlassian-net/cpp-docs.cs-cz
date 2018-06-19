---
title: -WINMDFILE (určení souboru klíče winmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba19ddd7a9ca1c313cc9f72e6cc8b77b4b565ceb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375633"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDFILE (Určení souboru klíče winmd)
Určuje klíč nebo pár klíčů k podepsání souboru metadat Windows Runtime (.winmd).  
  
```  
/WINMDKEYFILE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 Vypadá takto: [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) – možnost linkeru použitý pro soubor .winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **metadat Windows** stránku vlastností.  
  
4.  V **soubor klíče metadat Windows** zadejte umístění souboru.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)