---
title: /KEYFILE (Zadat klíč nebo pár klíčů pro podepsání sestavení)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: 279f83dd66777c0f1bb0aca836808da196886281
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414730"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Zadat klíč nebo pár klíčů pro podepsání sestavení)

```
/KEYFILE:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Soubor, který obsahuje klíč. Vložit do dvojitých uvozovek ("") Pokud obsahuje mezery.

## <a name="remarks"></a>Poznámky

Linker vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* na příkazovém řádku. Podepsané sestavení se říká, že chcete mít silný název.

Pokud kompilujete s [/LN](../../build/reference/ln-create-msil-module.md), je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení, které obsahuje explicitní odkaz na modul, prostřednictvím [#using](../../preprocessor/hash-using-directive-cpp.md), nebo při propojování s [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).

Můžete také předat údaje o šifrování linkeru s [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md). Použití [/delaysign](../../build/reference/delaysign-partially-sign-an-assembly.md) potřebujete částečně podepsaného sestavení. Zobrazit [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Další informace o podepisování sestavení.

V případě obě **/keyfile** a **/keycontainer** zadávají (pomocí parametru příkazového řádku nebo pomocí vlastního atributu), linker se nejdřív pokusí použít kontejner klíčů. Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů. Pokud linker kontejner klíčů nenajde, pokusí se soubor určený parametrem/keyfile. Pokud se tato operace úspěšná, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči budou nainstalovány do kontejneru klíčů (podobné sn -i) tak, aby při další kompilaci bude platný kontejner klíčů.

Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.

Zobrazit [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) Další informace o podepisování sestavení.

Další možnosti linkeru, které ovlivňují generování sestavení jsou:

- [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
