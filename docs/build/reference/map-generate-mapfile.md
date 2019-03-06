---
title: /MAP (Generovat soubor mapování)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 769fdc6a3980be34d92fc722099fde11ab677dc8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417889"
---
# <a name="map-generate-mapfile"></a>/MAP (Generovat soubor mapování)

```
/MAP[:filename]
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Uživatelem zadaný název souboru mapfile. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Parametr/map přikazuje linkeru, aby vytvořil soubor mapy.

Ve výchozím nastavení linker názvy souboru mapfile se základním názvem programu a .map rozšíření. Volitelný *filename* umožňuje přepsat výchozí název pro soubor mapfile.

Souboru mapování je textový soubor, který obsahuje následující informace o propojovaném programu:

- Název modulu, což je základní název souboru

- Časové razítko ze záhlaví souboru programu (a ne pomocí systému souborů)

- Seznam skupin k aplikaci s každou skupinu počáteční adresa (jako *části*:*posun*), délka, název skupiny a třídy

- Seznam veřejné symboly, s každou adresu (jako *části*:*posun*), symbol souboru .obj, kde je definován symbol, název a adresu bez stromové struktury

- Vstupní bod (jako *části*:*posun*)

[Parametr/MapInfo](../../build/reference/mapinfo-include-information-in-mapfile.md) možnost určuje další informace, které mají být zahrnuty v souboru mapfile.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **generovat soubor mapy** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
