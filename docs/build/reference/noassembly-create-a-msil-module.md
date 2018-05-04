---
title: -NOASSEMBLY (vytvořit modul MSIL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NOASSEMBLY
- VC.Project.VCLinkerTool.TurnOffAssemblyGeneration
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- -NOASSEMBLY linker option
- /NOASSEMBLY linker option
- NOASSEMBLY linker option
- assemblies [C++], not creating an assembly
ms.assetid: 3cea4e70-f451-4395-a626-1930b1b127fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44cc95186c6bb0071d2fa40bb70e41679736dcdd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="noassembly-create-a-msil-module"></a>/NOASSEMBLY (Vytvořit modul MSIL)
```  
/NOASSEMBLY  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /NOASSEMBLY informuje linkeru pro vytvoření image pro aktuální soubor výstupu bez sestavení rozhraní .NET Framework. Výstupní soubor MSIL bez manifest sestavení se nazývá modul.  
  
 Ve výchozím nastavení se vytvoří sestavení. Můžete také [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md) – možnost kompilátoru vytvořit modul.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **zapnout vypnout vytváření sestavení** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TurnOffAssemblyGeneration%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)