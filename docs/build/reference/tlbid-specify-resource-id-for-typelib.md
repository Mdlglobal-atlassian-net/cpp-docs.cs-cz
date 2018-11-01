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
ms.openlocfilehash: 1a86c753aa94302e7f4d26c53fee2f63175d33c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519285"
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

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)