---
title: -DEFAULTLIB (zadat výchozí knihovnu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e48db05ea50917a09e618c782d86dace73a1bf7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Zadat výchozí knihovnu)
```  
/DEFAULTLIB:library  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Knihovna*  
 Název knihovnu, kterou chcete hledat při rozpoznávání externí odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /DEFAULTLIB přidá jeden *knihovny* do seznamu knihovny, které odkaz vyhledá při rozpoznávání odkazy. Prohledají se zadaným /DEFAULTLIB knihovny po zadat na příkazovém řádku a před výchozí knihovny s názvem v soubory .obj knihovny.  
  
 [Ignorovat všechny výchozí knihovny](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB) možnost přepsání /DEFAULTLIB:*knihovny*. [Ignorovat knihovny](../../build/reference/nodefaultlib-ignore-libraries.md) (/ NODEFAULTLIB:*knihovny*) možnost přepsání /DEFAULTLIB:*knihovny* při stejné *knihovny* je název zadaný v obou.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
-   Tato možnost linkeru není k dispozici z vývojovém prostředí sady Visual Studio. K přidání do knihovny do fáze propojení, použijte **Další závislosti** vlastnost z **vstup** stránku vlastností.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)