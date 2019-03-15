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
ms.openlocfilehash: 728e8a84ff8d1afac99f99dbb975c7fd9360bcc1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815252"
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

1. Vytvoření modulu s [/LN](ln-create-msil-module.md).

1. Použijte /ASSEMBLYMODULE v jiném projektu k zahrnutí modulu v aktuální kompilaci, která se vytvoří sestavení. Tento projekt nebude odkazovat na modul s parametrem `#using`.

1. Jakýkoli projekt, který odkazuje na toto sestavení teď můžete také použít typy z modulu.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/ KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

MSVC linker přijímá soubory .netmodule jako vstup a výstup souboru vytvořený pomocí linkeru bude sestavení nebo modul .NET s za běhu závislost na některý z modulů .NET, které byly vstup do linkeru.  Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **přidat modul do sestavení** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
