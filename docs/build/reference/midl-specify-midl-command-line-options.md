---
title: /MIDL (Zadejte možnosti příkazového řádku MIDL)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492712"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Zadejte možnosti příkazového řádku MIDL)

Určuje soubor odezvy pro možnosti příkazového řádku MIDL.

## <a name="syntax"></a>Syntaxe

> **/MIDL:\@** <em>soubor</em>

## <a name="arguments"></a>Arguments

*souborů*<br/>
Název souboru, který obsahuje [Možnosti příkazového řádku MIDL](/windows/win32/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Poznámky

Všechny možnosti pro převod souboru IDL na soubor. TLB musí být uvedeny v *souboru*. Možnosti příkazového řádku MIDL nejde zadat v příkazovém řádku linkeru. Pokud není zadán parametr/MIDL, kompilátor MIDL bude vyvolána pouze s názvem souboru IDL a bez dalších možností.

Soubor by měl obsahovat jednu možnost příkazového řádku MIDL na řádek.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1.  > VybertestránkuvlastnostílinkeruvloženéhoIDL. > 

1. Upravte vlastnost **příkazy MIDL** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[/IDLOUT (pojmenování výstupních souborů MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (pojmenování souboru .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)
