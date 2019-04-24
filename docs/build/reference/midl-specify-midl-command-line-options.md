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
ms.openlocfilehash: 584958ac51bdc491ad1bdd16117ecaad6e000ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321069"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Zadejte možnosti příkazového řádku MIDL)

Určuje soubor odpovědí pro možnosti příkazového řádku MIDL

## <a name="syntax"></a>Syntaxe

> **/ MIDL:\@**<em>souboru</em>

## <a name="arguments"></a>Arguments

*Soubor*<br/>
Název souboru, který obsahuje [možností příkazového řádku MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Poznámky

Všechny možnosti pro převod souboru IDL do vyrovnávací paměti TLB souboru musí být uvedené v *souboru*; Možnosti příkazového řádku MIDL nelze zadat na příkazovém řádku linkeru. Pokud není zadán /MIDL, kompilátor MIDL o tom bude vyvolán s pouze název souboru IDL a žádné jiné možnosti.

Soubor musí obsahovat jeden parametr příkazového řádku MIDL každý řádek.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **vložené IDL** stránku vlastností.

1. Upravit **příkazy MIDL** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[/IDLOUT (pojmenování výstupních souborů MIDL)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (pojmenování souboru .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)
