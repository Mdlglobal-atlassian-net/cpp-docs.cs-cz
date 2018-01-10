---
title: "-MERGE (kombinované oddíly) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /merge
- VC.Project.VCLinkerTool.MergeSections
dev_langs: C++
helpviewer_keywords:
- sections, combining
- /MERGE linker option
- sections, naming
- sections
- -MERGE linker option
- MERGE linker option
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9da4258c1f2b45b2ad6a0dbe3c57cc5f1f304cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="merge-combine-sections"></a>/MERGE (kombinované oddíly)
```  
/MERGE:from=to  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/Merge kombinuje první část (*z*) s druhou část (*k*), názvy výsledná část *k*. Například `/merge:.rdata=.text`.  
  
 Pokud se druhá část neexistuje, odkazu přejmenuje části *z* jako *k*.  
  
 / Merge možnost je užitečná pro vytváření ovladače VxD a přepsání názvy generované kompilátorem částí.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **sloučení oddílů** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)