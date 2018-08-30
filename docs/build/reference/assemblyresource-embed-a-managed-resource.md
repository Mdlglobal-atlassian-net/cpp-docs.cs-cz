---
title: -ASSEMBLYRESOURCE (vložení spravovaného prostředku) | Dokumentace Microsoftu
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
ms.openlocfilehash: acb7b173ffd22e65e20dcc9cceef61b2e2131c83
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213398"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (integrovaný spravovaný zdroj)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Parametry  
 *Název souboru*  
 Spravovaný prostředek, který chcete vložit do tohoto sestavení.  
  
 *Jméno*  
 Volitelné. Logický název prostředku. Název používaný k načtení prostředku. Výchozí hodnota je název souboru.  
  
 Volitelně můžete zadat, pokud soubor by měl být privátní v manifestu sestavení. Ve výchozím nastavení *název* veřejnou v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí možnosti narozdíl od prostředek pro vložení do sestavení.  
  
 Prostředky jsou v sestavení při vytvořené pomocí linkeru veřejné. Linker neumožňuje přejmenovat prostředků v sestavení.  
  
 Pokud *filename* je soubor prostředků (.resources) rozhraní .NET Framework vytvořený, například podle [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z **System.Resources** obor názvů (viz [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx) Další informace). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** pro přístup k prostředku v době běhu.  
  
 Další možnosti linkeru, které ovlivňují generování sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **Linkeru** složky.  
  
3.  Klikněte na tlačítko **vstup** stránku vlastností.  
  
4.  Upravit **vložit soubor spravovaných prostředků** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)