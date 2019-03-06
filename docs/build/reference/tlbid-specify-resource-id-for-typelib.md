---
title: /TLBID (Zadat ID zdroje pro TypeLib)
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: b65ef73e2c7802b960b8480fff83c96fbe869293
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426469"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Zadat ID zdroje pro TypeLib)

```
/TLBID:id
```

## <a name="arguments"></a>Arguments

*id*<br/>
Hodnota zadané uživatelem pro knihovnu typů vytvoří linker. Přepíše výchozí ID prostředku 1.

## <a name="remarks"></a>Poznámky

Při kompilaci programu, který používá atributy, linker vytvoří knihovnu typů. Linker přiřadí ID prostředku z 1 na knihovnu typů.

Pokud toto ID prostředku je v konfliktu s některou z existujících prostředků, můžete zadat jiné ID s /TLBID. Rozsah hodnot, které můžete předat `id` je 1 až 65535.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **ID prostředku knihovny typů** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
