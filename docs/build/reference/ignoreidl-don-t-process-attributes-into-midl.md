---
title: "-IGNOREIDL (Tento & č. 39; atributy proces t do MIDL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs: C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe2f1d33f9269380bf0d914d5805cce3b0a92b90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/ IGNOREIDL (Tento & č. 39; atributy proces t do MIDL)
```  
/IGNOREIDL  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /IGNOREIDL Určuje, že jakékoli [IDL – atributy](../../windows/idl-attributes.md) ve zdroji nesmí kód do souboru IDL zpracovat.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Embedded IDL** stránku vlastností.  
  
4.  Změnit **ignorovat Embedded IDL** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ IDLOUT (pojmenovat výstupní soubory MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ TLBOUT (název. Soubor TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [/ MIDL (zadejte možnosti příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Sestavení programu s atributy](../../windows/building-an-attributed-program.md)