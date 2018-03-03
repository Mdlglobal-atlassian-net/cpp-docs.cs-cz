---
title: "-TLBOUT (název. Soubor TLB) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c898121a4ac29cc05022504ebfe33949b44eca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Název souboru .TLB)
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Cesta*  
 Specifikace absolutní nebo relativní cestu pro kde by měl být vytvořen souboru .tlb.  
  
 *Název souboru*  
 Určuje název souboru .tlb vytvořené MIDL kompilátoru. Předpokládá se bez přípony souboru; Zadejte *filename*.tlb, pokud chcete, aby .tlb rozšíření.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /TLBOUT Určuje název a příponu souboru .tlb.  
  
 Volá MIDL kompilátoru linkeru jazyka Visual C++ při propojování projekty, které mají [modulu](../../windows/module-cpp.md) atribut.  
  
 Pokud není zadán /TLBOUT, souboru .tlb dostane jeho název z [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*. Pokud /IDLOUT není zadán, bude mít název vc70.tlb souboru .tlb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Embedded IDL** stránku vlastností.  
  
4.  Změnit **knihovny typů** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ IGNOREIDL (Nezpracovávat atributy v MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ MIDL (zadejte možnosti příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Sestavení programu s atributy](../../windows/building-an-attributed-program.md)