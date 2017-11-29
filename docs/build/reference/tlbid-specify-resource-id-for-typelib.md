---
title: -TLBID (zadat ID zdroje pro TypeLib) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
dev_langs: C++
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9a260882b7e4623149e9e82a3a635f7230b6985a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Zadat ID zdroje pro TypeLib)
```  
/TLBID:id  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `id`  
 Hodnota zadaného uživatelem pro knihovny typů vytvořené linkeru. Přepíše výchozí ID prostředku 1.  
  
## <a name="remarks"></a>Poznámky  
 Při kompilování program, který používá atributy, vytvoří linkeru knihovny typů. Linkeru přiřadí ID prostředku 1 ke knihovně typů.  
  
 Pokud ID prostředku je v konfliktu s jedním z existujících prostředků, můžete zadat jinou ID s /TLBID. Rozsah hodnot, které můžete předat do `id` je 1 až 65535.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Embedded IDL** stránku vlastností.  
  
4.  Změnit **ID prostředku knihovny TypeLib** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)