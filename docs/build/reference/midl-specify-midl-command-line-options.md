---
title: -MIDL (určení možností příkazového řádku MIDL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2fa03920f60d7da4730bc46b23605ccfa13f6d7
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860379"
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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **vložené IDL** stránku vlastností.

1. Upravit **příkazy MIDL** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[/IDLOUT (pojmenování výstupních souborů MIDL)](../../build/reference/idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (pojmenování souboru .TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)
