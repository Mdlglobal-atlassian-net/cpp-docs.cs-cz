---
title: /ASSEMBLYRESOURCE (integrovaný spravovaný zdroj)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: c18a014ca645cceb3196fb7efefd227e96f8e1fa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416213"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (integrovaný spravovaný zdroj)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Parametry

*Název souboru*<br/>
Spravovaný prostředek, který chcete vložit do tohoto sestavení.

*Jméno*<br/>
Volitelné. Logický název prostředku. Název používaný k načtení prostředku. Výchozí hodnota je název souboru.

Volitelně můžete zadat, pokud soubor by měl být privátní v manifestu sestavení. Ve výchozím nastavení *název* veřejnou v sestavení.

## <a name="remarks"></a>Poznámky

Pomocí možnosti narozdíl od prostředek pro vložení do sestavení.

Prostředky jsou v sestavení při vytvořené pomocí linkeru veřejné. Linker neumožňuje přejmenovat prostředků v sestavení.

Pokud *filename* je soubor prostředků (.resources) rozhraní .NET Framework vytvořený, například podle [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z **System.Resources** obor názvů (viz [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager) Další informace). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** pro přístup k prostředku v době běhu.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **vložit soubor spravovaných prostředků** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
