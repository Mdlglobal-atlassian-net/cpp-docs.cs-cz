---
title: "-PGD (určit databázi pro optimalizace na základě profilu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb61395d9f3b8c98e17e3683a7c3897b9315d78b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Určit databázi pro optimalizace na základě profilu)
/ PGD:`filename`  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `filename`  
 Určuje název souboru .pgd, který se použije k uložení informací o spuštěného programu.  
  
## <a name="remarks"></a>Poznámky  
 Při použití [/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md), zadejte jiný než výchozí název nebo umístění souboru .pgd pomocí /PGD. Pokud nezadáte /PGD, název souboru .pgd stejný jako název výstupního souboru (.exe nebo .dll) a vytvoří se ve stejném adresáři, ze kterého byl vyvolán odkaz.  
  
 Při použití /LTCG:PGOPTIMIZE, zadejte název souboru .pgd sloužící k vytvoření optimalizované bitové kopie pomocí /PGD.  
  
 Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **optimalizace** stránku vlastností.  
  
5.  Změnit **databáze na základě profilu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)