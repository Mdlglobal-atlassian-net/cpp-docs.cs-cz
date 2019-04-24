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
ms.openlocfilehash: 1eac489ffd01f6bd79fc8c5bbda23adb751c9486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295068"
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

- [/ ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/ KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **vložit soubor spravovaných prostředků** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
