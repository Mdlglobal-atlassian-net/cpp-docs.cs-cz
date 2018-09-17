---
title: -TLBOUT (název. Soubor vyrovnávací paměti TLB) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c44028f834d2b3200b970fdc613d0bf4d4efd29
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702855"
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

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/ IGNOREIDL (Nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)
[/MIDL (určení možností příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[sestavení programu s atributy](../../windows/building-an-attributed-program.md)