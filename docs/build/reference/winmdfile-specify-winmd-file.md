---
title: /WINMDFILE (Určení souboru winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5d24d1d1aad8442f549dcb1aa4bd6414070c282c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316480"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (Určení souboru winmd)

Určuje název souboru výstupního souboru Windows Runtime Metadata (.winmd), který je generován [winmd](winmd-generate-windows-metadata.md) – možnost linkeru.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Poznámky

Použijte hodnotu ve stanoveném `filename` přepsat výchozí název souboru .winmd (`binaryname`.winmd). Všimněte si, že ".winmd" nepřipojujte k `filename`.  Pokud více hodnot, které jsou uvedeny na **/WINMDFILE** příkazovým řádkem, poslední z nich má přednost.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **soubor metadat Windows** zadejte umístění souboru.

## <a name="see-also"></a>Viz také:

[/WINMD (generování metadat Windows)](winmd-generate-windows-metadata.md)<br/>
[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
