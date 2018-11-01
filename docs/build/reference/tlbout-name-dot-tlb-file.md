---
title: /TLBOUT (Název souboru .TLB)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 97659341d4566cd34fe705b89758929f0c1e995d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613808"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Název souboru .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Arguments

*Cesta*<br/>
Specifikaci absolutní nebo relativní cestu, pro kterého chcete vytvořit souboru .tlb.

*Název souboru*<br/>
Určuje název souboru .tlb vytvořený kompilátorem MIDL. Předpokládá se bez přípony souboru; Zadejte *filename*.tlb, pokud chcete s příponou .tlb.

## <a name="remarks"></a>Poznámky

/ Tlbout Určuje název a příponu souboru tlb.

V kompilátoru MIDL je volán linkeru jazyka Visual C++ při propojování projekty, které mají [modulu](../../windows/module-cpp.md) atribut.

/TLBOUT není zadán, souboru .tlb dojde k jeho název z [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*. Pokud /IDLOUT není zadán, bude mít název vc70.tlb souboru .tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **knihovny typů** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (určení možností příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)