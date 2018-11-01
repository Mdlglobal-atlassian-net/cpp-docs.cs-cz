---
title: /WINMDFILE (Určení souboru winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 74958e51925b9ed6d1382efe76fe587eed73f4e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656051"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (Určení souboru winmd)

Určuje název souboru výstupního souboru Windows Runtime Metadata (.winmd), který je generován [winmd](../../build/reference/winmd-generate-windows-metadata.md) – možnost linkeru.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Poznámky

Použijte hodnotu ve stanoveném `filename` přepsat výchozí název souboru .winmd (`binaryname`.winmd). Všimněte si, že ".winmd" nepřipojujte k `filename`.  Pokud více hodnot, které jsou uvedeny na **/WINMDFILE** příkazovým řádkem, poslední z nich má přednost.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **soubor metadat Windows** zadejte umístění souboru.

## <a name="see-also"></a>Viz také

[/WINMD (generování metadat Windows)](../../build/reference/winmd-generate-windows-metadata.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)