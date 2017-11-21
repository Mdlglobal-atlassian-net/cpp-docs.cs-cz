---
title: "-MIDL (zadejte možnosti příkazového řádku MIDL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs: C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 957d9679c57cd15162c5820ccd7dc41bdea0fa2d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Zadejte možnosti příkazového řádku MIDL)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `file`  
 Název souboru, který obsahuje [možnosti příkazového řádku MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## <a name="remarks"></a>Poznámky  
 Všechny možnosti pro převod soubor IDL TLB souboru musí mít `file`; Možnosti příkazového řádku MIDL nelze zadat na příkazovém řádku linkeru. Pokud není zadán /MIDL, MIDL kompilátoru bude vyvolán s pouze název souboru IDL a žádné jiné možnosti.  
  
 Soubor by měl obsahovat jednu možnost příkazového řádku MIDL na každý řádek.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Embedded IDL** stránku vlastností.  
  
4.  Změnit **MIDL příkazy** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ IDLOUT (pojmenovat výstupní soubory MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ IGNOREIDL (Nezpracovávat atributy v MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ TLBOUT (název. Soubor TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Sestavení programu s atributy](../../windows/building-an-attributed-program.md)