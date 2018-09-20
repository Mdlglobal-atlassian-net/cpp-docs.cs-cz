---
title: -IDLOUT (pojmenování výstupních souborů MIDL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef4f8b418edcdb903fa8f807cb5e08d63eaeeed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441626"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Pojmenovat výstupní soubory MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Parametry

*Cesta*<br/>
Specifikaci absolutní nebo relativní cestu. Zadáním cesty ovlivňují pouze umístění souboru IDL; všechny ostatní soubory jsou umístěny v adresáři projektu.

*Název souboru*<br/>
Určuje název souboru .idl vytvořený kompilátorem MIDL. Předpokládá se bez přípony souboru; Zadejte *filename*.idl, pokud chcete rozšíření IDL.

## <a name="remarks"></a>Poznámky

/ Idlout Určuje název a příponu souboru IDL.

V kompilátoru MIDL je volán linkeru jazyka Visual C++ při propojování projekty, které mají [modulu](../../windows/module-cpp.md) atribut.

/ IDLOUT určuje také názvy souborů ostatních výstupních souborů spojené s kompilátorem MIDL:

- *Název souboru*.tlb

- *Název souboru*_p.c

- *Název souboru*_i.c

- *Název souboru*.h

*Název souboru* je parametr, který můžete předat /IDLOUT. Pokud [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md) není zadána, panelu /TLBOUT zobrazí jeho název souboru .tlb *filename*.

Pokud nezadáte /IDLOUT ani /TLBOUT, linker vytvoří vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c a vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **sloučení IDL základní název souboru** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (určení možností příkazového řádku MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)