---
title: -MIDL (určení možností příkazového řádku MIDL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3f20fddd657d1e5e57caf65ecc8e2c52afbf12
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466201"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Zadejte možnosti příkazového řádku MIDL)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `file`  
 Název souboru, který obsahuje [možností příkazového řádku MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## <a name="remarks"></a>Poznámky  
 Všechny možnosti pro převod souboru IDL do vyrovnávací paměti TLB souboru musí být uvedené v `file`; Možnosti příkazového řádku MIDL nelze zadat na příkazovém řádku linkeru. Pokud není zadán /MIDL, kompilátor MIDL o tom bude vyvolán s pouze název souboru IDL a žádné jiné možnosti.  
  
 Soubor musí obsahovat jeden parametr příkazového řádku MIDL každý řádek.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **Linkeru** složky.  
  
3.  Klikněte na tlačítko **vložené IDL** stránku vlastností.  
  
4.  Upravit **příkazy MIDL** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ IDLOUT (pojmenování výstupních souborů MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/ IGNOREIDL (Nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ TLBOUT (název. Soubor vyrovnávací paměti TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Sestavení programu s atributy](../../windows/building-an-attributed-program.md)