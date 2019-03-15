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
ms.openlocfilehash: d309390c1ac1a19d9d4a982908dbbbac0bd52714
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813770"
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

Pokud kompilujete s [/LN](ln-create-msil-module.md), je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení, které obsahuje explicitní odkaz na modul, prostřednictvím [#using](../../preprocessor/hash-using-directive-cpp.md), nebo při propojování s [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

Můžete také předat údaje o šifrování linkeru s [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md). Použití [/delaysign](delaysign-partially-sign-an-assembly.md) potřebujete částečně podepsaného sestavení. Zobrazit [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Další informace o podepisování sestavení.

V případě obě **/keyfile** a **/keycontainer** zadávají (pomocí parametru příkazového řádku nebo pomocí vlastního atributu), linker se nejdřív pokusí použít kontejner klíčů. Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů. Pokud linker kontejner klíčů nenajde, pokusí se soubor určený parametrem/keyfile. Pokud se tato operace úspěšná, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči budou nainstalovány do kontejneru klíčů (podobné sn -i) tak, aby při další kompilaci bude platný kontejner klíčů.

Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.

Zobrazit [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) Další informace o podepisování sestavení.

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

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
