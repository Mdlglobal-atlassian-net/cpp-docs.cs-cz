---
title: /ASSEMBLYLINKRESOURCE (Vytvořit odkaz na prostředek rozhraní .NET Framework)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: fb707a2721ed40ee3ec37d01b2bbcfcc51f05c38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295159"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Vytvořit odkaz na prostředek rozhraní .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Soubor prostředků rozhraní .NET Framework, na který chcete propojit ze sestavení.

## <a name="remarks"></a>Poznámky

/ ASSEMBLYLINKRESOURCE vytvoří odkaz na prostředek rozhraní .NET Framework do výstupního souboru; soubor prostředků není umístěn do výstupního souboru. [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) do výstupního souboru vloží soubor prostředku.

Propojené prostředky byly veřejné sestavení při vytvořené pomocí linkeru.

/ ASSEMBLYLINKRESOURCE vyžaduje, aby kompilace [/CLR](clr-common-language-runtime-compilation.md); [/LN](ln-create-msil-module.md) nebo [parametr/noassembly](noassembly-create-a-msil-module.md) není povolen u /ASSEMBLYLINKRESOURCE.

Pokud *filename* je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z **System.Resources** oboru názvů. Další informace najdete v tématu [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager). U všech ostatních prostředků, použijte **GetManifestResource** \* metody v **System.Reflection.Assembly** pro přístup k prostředku v době běhu.

*Název souboru* může být libovolný formát souboru. Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, abyste mohli nainstalovat do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
