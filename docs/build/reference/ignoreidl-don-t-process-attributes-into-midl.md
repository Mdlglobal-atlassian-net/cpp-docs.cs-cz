---
title: / IGNOREIDL (Don&#39;t procesu atributy do MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: f6c5fcbae52ed695f2d0c389607ac4231f069788
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534352"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/ IGNOREIDL (Don&#39;t procesu atributy do MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Poznámky

/ Ignoreidl Určuje, že všechny [IDL – atributy](../../windows/idl-attributes.md) ve zdroji kódu nemají být zpracovány do souboru IDL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **ignorovat vložené IDL** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/IDLOUT (pojmenování výstupních souborů MIDL)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/TLBOUT (pojmenování souboru .TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (určení možností příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)