---
title: -VERSION (informace o verzi) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
dev_langs: C++
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a0792a3895aac2887e635cb300f8ba9fde67e97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="version-version-information"></a>/VERSION (informace o verzi)
```  
/VERSION:major[.minor]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *hlavní*a *menší*  
 Číslo verze, které chcete v záhlaví souboru .exe nebo .dll.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /VERSION informuje linkeru uvést číslo verze v hlavičce souboru .exe nebo .dll. Použijte DUMPBIN [/HEADERS](../../build/reference/headers.md) zobrazíte pole verze bitové kopie volitelné hodnoty HLAVIČKY tak, aby se projevily /VERSION.  
  
 *Hlavní* a *menší* argumenty jsou desítková číslice v rozsahu 0 až 65 535. Výchozí hodnota je verze 0,0.  
  
 Informace o zadaným /VERSION nemá vliv na informace o verzi, která se zobrazí pro aplikaci po zobrazte její vlastnosti v Průzkumníku souborů. Informace o této verzi pochází ze zdrojového souboru, který je použit k vytvoření aplikace. V tématu [Editor informací o verzi](../../windows/version-information-editor.md) Další informace.  
  
 Je také možné vložit číslo verze se [verze](../../build/reference/version-c-cpp.md) příkaz definice modulu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Obecné** stránku vlastností.  
  
4.  Změnit **verze** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)