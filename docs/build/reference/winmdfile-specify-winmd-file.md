---
title: -WINMDFILE (určení souboru winmd) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d34bdfd2d80690efae8efbc1f95ba0c50a530af3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425779"
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