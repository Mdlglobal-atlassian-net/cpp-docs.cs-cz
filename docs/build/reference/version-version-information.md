---
title: /VERSION (informace o verzi)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 709ba836fb537fbcb594f7eb6aa2f2d43df5b4d1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414704"
---
# <a name="version-version-information"></a>/VERSION (informace o verzi)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>Arguments

*hlavní* a *podverze*<br/>
Číslo verze, které chcete v hlavičce souboru .exe nebo .dll.

## <a name="remarks"></a>Poznámky

Parametr/Version přikáže linkeru, aby vložil číslo verze v hlavičce souboru .exe nebo .dll. Pomocí DUMPBIN [/HEADERS](../../build/reference/headers.md) zobrazíte pole verze image OPTIONAL HEADER VALUES a posoudit účinek parametru/Version.

*Hlavní* a *menší* argumenty jsou desetinná čísla v rozsahu 0 až 65535. Výchozí hodnota je verze 0,0.

Informace o zadaný s/Version nemá vliv informace o verzi, která se zobrazí aplikace, když zobrazíte její vlastnosti v Průzkumníku souborů. Informace o této verzi pocházejí ze souboru prostředků, který se používá k sestavení aplikace. Zobrazit [Editor informací o verzi](../../windows/version-information-editor.md) Další informace.

Dalším způsobem, jak vložit číslo verze se [verze](../../build/reference/version-c-cpp.md) příkaz definice modulu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **verze** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
