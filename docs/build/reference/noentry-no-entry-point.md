---
title: -NOENTRY (bez vstupního bodu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
dev_langs:
- C++
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd90cb7824050e9bd0110e75f7120c4f004b8b47
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713463"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (bez vstupního bodu)

```
/NOENTRY
```

## <a name="remarks"></a>Poznámky

Parametr/NOENTRY je vyžadována pro vytvoření knihovny DLL pouze prostředků, která neobsahuje žádný spustitelný kód. Další informace najdete v tématu [vytváření knihovny DLL Resource-Only](../../build/creating-a-resource-only-dll.md).

Tuto možnost použijte, chcete-li zabránit nástroji LINK v propojení odkazu na metodu `_main` do knihovny DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **Upřesnit** stránku vlastností.

1. Upravit **bez vstupního bodu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Viz také

[Vytvoření knihovny DLL obsahující jen prostředky](../../build/creating-a-resource-only-dll.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)