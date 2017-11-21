---
title: "-ASSEMBLYLINKRESOURCE (vytvořit odkaz na prostředek rozhraní .NET Framework) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs: C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a0042b85117a00ff82a96937d2cfd68e3b98203
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Vytvořit odkaz na prostředek rozhraní .NET Framework)
```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Soubor prostředků rozhraní .NET Framework, do kterého chcete propojit ze sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Možnost /ASSEMBLYLINKRESOURCE vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru; soubor prostředků není umístěn ve výstupním souboru. [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) vloží soubor prostředků ve výstupním souboru.  
  
 Jsou propojené prostředky veřejné v sestavení při vytvoření s linkeru.  
  
 / ASSEMBLYLINKRESOURCE vyžaduje, aby kompilace [/CLR](../../build/reference/clr-common-language-runtime-compilation.md); [/LN](../../build/reference/ln-create-msil-module.md) nebo [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) není povolen u /ASSEMBLYLINKRESOURCE.  
  
 Pokud *filename* je soubor prostředků rozhraní .NET Framework, který je vytvořen, například pomocí [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí k němu se členy v **System.Resources** oboru názvů. Další informace najdete v tématu [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** třídy pro přístup k prostředku v době běhu.  
  
 *Název souboru* může být jakékoli formát souboru. Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, může být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)