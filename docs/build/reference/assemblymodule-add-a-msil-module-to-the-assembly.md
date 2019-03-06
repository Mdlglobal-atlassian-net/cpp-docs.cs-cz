---
title: /ASSEMBLYMODULE (přidání modulu MSIL do sestavení)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: 567ec4b1e773e8aa4ff248c7bb110cfb594f089e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416693"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (přidání modulu MSIL do sestavení)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Modul, který chcete zahrnout do tohoto sestavení.

## <a name="remarks"></a>Poznámky

Assemblymodule umožňuje přidat odkaz modulu na sestavení. Informace o typu v modulu nebudou mít k dispozici sestavení program, který přidá odkaz na modul. Informace o typu v modulu však budou dostupné všem programům, které odkazuje na sestavení.

Použití [#using](../../preprocessor/hash-using-directive-cpp.md) přidat odkaz modulu na sestavení i k sestavení programu zpřístupnění informací o typu modulu.

Představte si třeba následující scénář:

1. Vytvoření modulu s [/LN](../../build/reference/ln-create-msil-module.md).

1. Použijte /ASSEMBLYMODULE v jiném projektu k zahrnutí modulu v aktuální kompilaci, která se vytvoří sestavení. Tento projekt nebude odkazovat na modul s parametrem `#using`.

1. Jakýkoli projekt, který odkazuje na toto sestavení teď můžete také použít typy z modulu.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Linkeru jazyka Visual C++ přijímá soubory .netmodule jako vstup a výstup souboru vytvořený pomocí linkeru bude sestavení nebo modul .NET s za běhu závislost na některý z modulů .NET, které byly vstup do linkeru.  Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **přidat modul do sestavení** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
