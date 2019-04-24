---
title: /IDLOUT (Pojmenovat výstupní soubory MIDL)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 3816bb85cb3c711075e3fefeec2d706c2f8cc2ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291571"
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

V kompilátoru MIDL je volán linkeru MSVC při propojování projekty, které mají [modulu](../../windows/module-cpp.md) atribut.

/ IDLOUT určuje také názvy souborů ostatních výstupních souborů spojené s kompilátorem MIDL:

- *Název souboru*.tlb

- *filename*_p.c

- *Název souboru*_i.c

- *Název souboru*.h

*Název souboru* je parametr, který můžete předat /IDLOUT. Pokud [/TLBOUT](tlbout-name-dot-tlb-file.md) není zadána, panelu /TLBOUT zobrazí jeho název souboru .tlb *filename*.

Pokud nezadáte /IDLOUT ani /TLBOUT, linker vytvoří vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c a vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **sloučení IDL základní název souboru** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (určení možností příkazového řádku MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)
