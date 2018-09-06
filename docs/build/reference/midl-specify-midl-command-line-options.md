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
ms.openlocfilehash: e513b0397a41a19c9a8088332eb3d1793b6b6647
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894587"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Zadejte možnosti příkazového řádku MIDL)

Určuje soubor odpovědí pro možnosti příkazového řádku MIDL

## <a name="syntax"></a>Syntaxe

> **/ MIDL:\@**<em>souboru</em>

## <a name="arguments"></a>Arguments

*Soubor*  
Název souboru, který obsahuje [možností příkazového řádku MIDL](/windows/desktop/Midl/general-midl-command-line-syntax).

## <a name="remarks"></a>Poznámky

Všechny možnosti pro převod souboru IDL do vyrovnávací paměti TLB souboru musí být uvedené v *souboru*; Možnosti příkazového řádku MIDL nelze zadat na příkazovém řádku linkeru. Pokud není zadán /MIDL, kompilátor MIDL o tom bude vyvolán s pouze název souboru IDL a žádné jiné možnosti.

Soubor musí obsahovat jeden parametr příkazového řádku MIDL každý řádek.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

2. Vyberte **vlastnosti konfigurace** > **Linkeru** > **vložené IDL** stránku vlastností.

3. Upravit **příkazy MIDL** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)   
[/ IDLOUT (pojmenování výstupních souborů MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
[/ IGNOREIDL (Nezpracovávat atributy do MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
[/ TLBOUT (název. Soubor vyrovnávací paměti TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)