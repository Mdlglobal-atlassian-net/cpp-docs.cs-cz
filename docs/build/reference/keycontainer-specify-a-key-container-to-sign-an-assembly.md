---
title: /KEYCONTAINER (Zadat kontejner klíčů pro podpis sestavení)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: 96d2f5fed0e450224f82ee909cea9d56082505fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291610"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Zadat kontejner klíčů pro podpis sestavení)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>Arguments

*Jméno*<br/>
Kontejner, který obsahuje klíč. Vložit do dvojitých uvozovek ("") Pokud obsahuje mezery.

## <a name="remarks"></a>Poznámky

Propojovací program vytvoří podepsané sestavení tak, že vloží veřejný klíč do manifestu sestavení a podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* na příkazovém řádku. **sériové číslo -i** nainstaluje pár klíčů do kontejneru.

Pokud kompilujete s [/LN](ln-create-msil-module.md), je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení, které obsahuje explicitní odkaz na modul, prostřednictvím [#using](../../preprocessor/hash-using-directive-cpp.md), nebo při propojování s [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

Můžete také předat údaje o šifrování pro kompilátor [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Použití [/delaysign](delaysign-partially-sign-an-assembly.md) potřebujete částečně podepsaného sestavení. Zobrazit [sestavení se silným názvem (podepisování sestavení) (C++vyhodnocovací)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Další informace o podepisování sestavení.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

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
