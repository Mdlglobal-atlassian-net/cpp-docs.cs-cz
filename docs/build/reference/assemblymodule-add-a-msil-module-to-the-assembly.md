---
title: "-ASSEMBLYMODULE (Přidání modulu MSIL do sestavení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efe45bd6a3225f50e1f842c6d247aae9626302a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (přidání modulu MSIL do sestavení)
```  
/ASSEMBLYMODULE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Modul, který chcete zahrnout do tohoto sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /ASSEMBLYMODULE umožňuje přidat odkaz na modul k sestavení. Informace o typu v modulu nebudou k dispozici na sestavení program, který přidat odkaz na modul. Informace o typu v modulu však bude k dispozici žádné program, který odkazuje na sestavení.  
  
 Použití [#using](../../preprocessor/hash-using-directive-cpp.md) jak přidat odkaz na modul k sestavení a zpřístupní informace o typu modulu programu sestavení.  
  
 Představte si třeba následující scénář:  
  
1.  Vytvoření modulu s [/LN](../../build/reference/ln-create-msil-module.md).  
  
2.  Použití /ASSEMBLYMODULE v různých projektu mají být zahrnuty v modulu aktuální kompilace, která vytvoří sestavení. Tento projekt nebude odkazovat na modul s `#using`.  
  
3.  Všechny projekt, který odkazuje toto sestavení teď můžete také použít typy z modulu.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Visual C++ linkeru .netmodule soubory akceptuje jako vstupní a výstupní soubor vyprodukované linkeru bude sestavení nebo .netmodule s už závislost běhu na žádném z .netmodules, že se vstupní linkeru.  Další informace najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **vstup** stránku vlastností.  
  
4.  Změnit **přidat modul sestavení** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)