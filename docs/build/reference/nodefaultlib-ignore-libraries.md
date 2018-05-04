---
title: -NODEFAULTLIB (Ignorovat knihovny) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs:
- C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51caac10218d5f4d1787b2256875001ac32dc2b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorovat knihovny)
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Knihovna*  
 Knihovna, která chcete linkeru ignorovat, pokud se přeloží externí odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /NODEFAULTLIB informuje linkeru odebrat jeden nebo více výchozí knihovny ze seznamu knihoven, které vyhledávání při rozpoznávání externí odkazy.  
  
 K vytvoření souboru .obj, který nebude obsahovat odkazy na výchozí knihovny, použijte [/Zl (vypuštění názvu výchozí knihovny)](../../build/reference/zl-omit-default-library-name.md).  
  
 Ve výchozím nastavení /NODEFAULTLIB odebere všechny výchozí knihovny ze seznamu knihoven, které vyhledávání při rozpoznávání externí odkazy. Volitelné *knihovny* parametr umožňuje odebrat ze seznamu knihoven vyhledávání při rozpoznávání externí odkazy uvedené knihovny nebo knihovny. Zadejte jednu možnost /NODEFAULTLIB pro každé knihovny, kterou chcete vyloučit.  
  
 Linkeru přeloží odkazy na externí definice prohledáním nejprve v knihovnách, které explicitně zadáte, a potom ve výchozích knihovny zadán pomocí parametru /DEFAULTLIB a potom v výchozí knihovny s názvem v soubory .obj.  
  
 / NODEFAULTLIB:*knihovny* přepsání [/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*knihovny* při stejné *knihovny* název je zadán v obou.  
  
 Pokud používáte /NODEFAULTLIB, například k sestavení vaší aplikace bez běhové knihovny jazyka C, může musíte také použít [/Entry](../../build/reference/entry-entry-point-symbol.md) k určení vstupního bodu (funkce) v programu. Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **vstup**stránku vlastností.  
  
4.  Vyberte **ignorovat všechny výchozí knihovny** vlastnost nebo zadat seznam knihoven, které chcete ignorovat v **ignorovat konkrétní knihovny** vlastnost. **Příkazového řádku** zobrazí stránku vlastností účinku změny provádět tyto vlastnosti.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)