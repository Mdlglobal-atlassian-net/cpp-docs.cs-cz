---
title: "-IDLOUT (pojmenovat výstupní soubory MIDL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs: C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f9f798c31fc4b492565c3406f0cb26251a208d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Pojmenovat výstupní soubory MIDL)
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>Parametry  
 *Cesta*  
 Specifikace absolutní nebo relativní cestu. Zadáním cesty ovlivňují jenom umístění souboru IDL; všechny ostatní soubory jsou umístěny v adresáři projektu.  
  
 *Název souboru*  
 Určuje název souboru .idl vytvořené MIDL kompilátoru. Předpokládá se bez přípony souboru; Zadejte *filename*.idl, pokud chcete, aby .idl rozšíření.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /IDLOUT Určuje název a příponu souboru .idl.  
  
 Volá MIDL kompilátoru linkeru jazyka Visual C++ při propojování projekty, které mají [modulu](../../windows/module-cpp.md) atribut.  
  
 / IDLOUT také určuje názvy souborů jiných výstupní soubory spojené s MIDL kompilátoru:  
  
-   *Název souboru*.tlb  
  
-   *Název souboru*_p.c  
  
-   *Název souboru*_i.c  
  
-   *Název souboru*.h  
  
 *Název souboru* je parametr, který můžete předat /IDLOUT. Pokud [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md) je zadán, a získávat její název souboru .tlb z /TLBOUT *filename*.  
  
 Pokud zadáte /IDLOUT ani /TLBOUT, linkeru vytvoří vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c a vc70.h.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Embedded IDL** stránku vlastností.  
  
4.  Změnit **sloučení název souboru IDL základní** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ IGNOREIDL (Nezpracovávat atributy v MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/ MIDL (zadejte možnosti příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Sestavení programu s atributy](../../windows/building-an-attributed-program.md)