---
title: /ASSEMBLYDEBUG (Přidat atribut DebuggableAttribute)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: 7e0a2133549a72fa747c67b40f9de1f8f48362b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426534"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Přidat atribut DebuggableAttribute)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ Parametr ASSEMBLYDEBUG generuje **DebuggableAttribute** atribut s ladicí informace o sledování a zakazuje optimalizace JIT. Toto je stejné jako zadání následující atribut ve zdroji:

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

Vysílá debuggable **DebuggableAttribute** atribut ale zakáže pro sledování informací o ladění a povolí optimalizace JIT. Toto je stejné jako zadání následující atribut ve zdroji:

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

Výchozí hodnota nelze vygenerovat **DebuggableAttribute** atribut.

DebuggableAttribute lze také přidat do sestavení přímo ve zdrojovém kódu. Například

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>Poznámky

Je potřeba explicitně zadat, že spravované image být laditelná. Pomocí [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) samostatně není dostatečná.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **Laditelné sestavení** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
