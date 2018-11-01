---
title: /LARGEADDRESSAWARE (zpracování velkých adres)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 6a83ac89c6ddf14885107193b32d9b7fe7853659
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543050"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (zpracování velkých adres)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>Poznámky

Parametr/LARGEADDRESSAWARE přikazuje linkeru, že aplikace dokáže zpracovat adresy větší než 2 GB. V 64bitové kompilátory je tato možnost povolená ve výchozím nastavení. V 32bitové kompilátory je povoleno: no, pokud na řádku linkeru není zadán parametr/LARGEADDRESSAWARE.

Pokud byla aplikace propojené s/LARGEADDRESSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) se zobrazí informace o tom.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Upravit **povolit velké adresy** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)