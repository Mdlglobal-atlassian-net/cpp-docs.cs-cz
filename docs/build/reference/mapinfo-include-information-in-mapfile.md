---
title: -MAPINFO (zahrnutí informaci do souboru mapování) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.MapLines
- VC.Project.VCLinkerTool.MapInfoFixups
- VC.Project.VCLinkerTool.MapExports
- /mapinfo
dev_langs:
- C++
helpviewer_keywords:
- /MAPINFO linker option
- MAPINFO linker option
- -MAPINFO linker option
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f52e044962007c4a820bf234d45b5cb9ffd584f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723083"
---
# <a name="mapinfo-include-information-in-mapfile"></a>/MAPINFO (Zahrnout informace do souboru mapování)

```
/MAPINFO:EXPORTS
```

## <a name="remarks"></a>Poznámky

Parametr/MapInfo přikazuje linkeru, aby začlenil zadané informace do souboru mapování, která je vytvořena při zadání [/MAP](../../build/reference/map-generate-mapfile.md) možnost.  Parametr EXPORTS přikazuje linkeru začlenit exportované funkce.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Změna **mapovat exporty** vlastnosti:

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)