---
title: -WINMD (generování metadat Windows) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b8b34e55fc0814653f4c44be50e545633be373
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705721"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (Generování metadat Windows)

Povolí generování souboru Windows Runtime Metadata (.winmd).

```
/WINMD[:{NO|ONLY}]
```

## <a name="remarks"></a>Poznámky

**/ WINMD**<br/>
Výchozí nastavení pro aplikace univerzální platformy Windows. Propojovací program vytvoří binární spustitelný soubor a soubor metadat .winmd.

**/WINMD:NO**<br/>
Linker generuje pouze binární spustitelný soubor, ale nejedná se o soubor winmd.

**/ WINMD: POUZE**<br/>
Linker generuje pouze soubor winmd, ale nikoli binární spustitelný soubor.

Ve výchozím nastavení, název výstupního souboru má tvar `binaryname`.winmd. Chcete-li zadat jiný název souboru, použijte [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) možnost.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **generování metadat Windows** rozevíracího seznamu vyberte požadovanou možnost.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)