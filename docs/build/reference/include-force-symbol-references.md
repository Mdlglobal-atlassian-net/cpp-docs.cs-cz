---
title: -INCLUDE (vynutit odkazy na symboly) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfe65344e41b98841c3a4e7bca72b762197510b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Vynutit odkazy na symboly)
```  
/INCLUDE:symbol  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 `symbol`  
 Určuje symbol, který se má přidat do tabulky symbolů.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /INCLUDE informuje linkeru pro přidání určený symbol do tabulky symbolů.  
  
 Pokud chcete zadat více symbolů, zadejte čárkou (,), středníkem (;) nebo mezery mezi názvy symbolů. Na příkazovém řádku zadejte /INCLUDE:`symbol` jednou pro každý symbol.  
  
 Přeloží linkeru `symbol` přidáním objekt, který obsahuje definici programu. Tato funkce je užitečná pro včetně objekt knihovny, které by jinak propojit k programu.  
  
 Zadání symbolu pomocí této možnosti přepsání odebrání tohoto symbolu podle [/OPT:REF](../../build/reference/opt-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **vstup** stránku vlastností.  
  
4.  Změnit **vynutit odkazy na symboly** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)