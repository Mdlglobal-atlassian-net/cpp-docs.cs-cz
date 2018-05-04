---
title: -ASSEMBLYRESOURCE (spravovaný prostředek pro vložení) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88afe292905ee46c1e939d29f787055f98058dc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (integrovaný spravovaný zdroj)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Parametry  
 *Název souboru*  
 Spravovaný prostředek, který chcete vložit v tomto sestavení.  
  
 *Jméno*  
 Volitelné. Logický název prostředku; název slouží k načtení prostředku. Výchozí hodnota je název souboru.  
  
 Volitelně můžete zadat, pokud soubor by měly být privátní v manifestu sestavení. Ve výchozím nastavení *název* je veřejný v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí možnosti /ASSEMBLYRESOURCE prostředek pro vložení do sestavení.  
  
 Prostředky jsou veřejné v sestavení při vytvoření s linkeru. Linkeru neumožňuje přejmenovat prostředků v sestavení.  
  
 Pokud *filename* je vytvořen, například pomocí souboru prostředků (.resources) rozhraní .NET Framework [Generátor zdrojových souborů (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí k němu se členy v **System.Resources** obor názvů (viz [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx) informace). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** třídy pro přístup k prostředku v době běhu.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **vstup** stránku vlastností.  
  
4.  Změnit **vložení spravované zdrojového souboru** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)