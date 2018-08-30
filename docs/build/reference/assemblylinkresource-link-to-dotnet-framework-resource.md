---
title: -ASSEMBLYLINKRESOURCE (odkaz na prostředek rozhraní .NET Framework) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs:
- C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e23bd9e0816c10f41e298afc9e82edbdd27e7a5f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206485"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Vytvořit odkaz na prostředek rozhraní .NET Framework)
```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Soubor prostředků rozhraní .NET Framework, na který chcete propojit ze sestavení.  
  
## <a name="remarks"></a>Poznámky  
 / ASSEMBLYLINKRESOURCE vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) do výstupního souboru vloží soubor prostředku.  
  
 Propojené prostředky byly veřejné sestavení při vytvořené pomocí linkeru.  
  
 / ASSEMBLYLINKRESOURCE vyžaduje, aby kompilace [/CLR](../../build/reference/clr-common-language-runtime-compilation.md); [/LN](../../build/reference/ln-create-msil-module.md) nebo [parametr/noassembly](../../build/reference/noassembly-create-a-msil-module.md) není povolen u /ASSEMBLYLINKRESOURCE.  
  
 Pokud *filename* je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z **System.Resources** oboru názvů. Další informace najdete v tématu [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** pro přístup k prostředku v době běhu.  
  
 *Název souboru* může být libovolný formát souboru. Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, abyste mohli nainstalovat do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.  
  
 Další možnosti linkeru, které ovlivňují generování sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **Linkeru** složky.  
  
3.  Klikněte na tlačítko **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)