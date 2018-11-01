---
title: /DELAYSIGN (částečně podepsané sestavení)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 233a41a3e55ff2726712541b0af9db1f5e55eb56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435617"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (částečně podepsané sestavení)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Arguments

**NE**<br/>
Určuje sestavení by neměly být částečně podepsáno.

## <a name="remarks"></a>Poznámky

Použití **/delaysign** Pokud chcete umístit veřejný klíč v sestavení. Výchozí hodnota je **/delaysign: No**.

**/Delaysign** možnost nemá žádný vliv, pokud nejsou použity s [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) nebo [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).

Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash pomocí soukromého klíče. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Pokud je sestavení podepisováno, linkeru a neukládá podpis, ale rezervuje prostor v souboru tak, že podpis se dají přidat později.

Například použití **/delaysign** umožňuje testerovi vložit sestavení do globální mezipaměti. Po otestování je možné plně podepsat sestavení tak, že privátní klíč v sestavení.

Zobrazit [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) a [zpožděné podepisování sestavení](/dotnet/framework/app-domains/delay-sign-assembly) Další informace o podepisování sestavení.

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

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)