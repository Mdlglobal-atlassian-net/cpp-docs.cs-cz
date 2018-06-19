---
title: / ALIGN (zarovnání oddílů) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs:
- C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 543ea30b06f62939f378167d8598c73f66061f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370303"
---
# <a name="align-section-alignment"></a>/ALIGN (zarovnání oddílů)

## <a name="syntax"></a>Syntaxe

> **/ ALIGN**[**:**_číslo_]

### <a name="arguments"></a>Arguments

*Číslo*  
Hodnota zarovnání v bajtech.

## <a name="remarks"></a>Poznámky

**/ALIGN** možnost určuje zarovnání každého oddílu v lineární adresní prostor programu. *Číslo* argument je v bajtech a musí být násobek dvou. Výchozí hodnota je 4K (4096). Linkeru vydá upozornění, pokud zarovnání vytvoří bitovou kopii neplatný.

Pokud píšete aplikace například ovladač zařízení, by neměl muset upravit zarovnání.

Je možné upravit zarovnání s parametrem align do určitého oddílu [/SECTION](../../build/reference/section-specify-section-attributes.md) možnost.

Zarovnání hodnotu, která zadáte nemůže být menší než největší zarovnání oddílů.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost v **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
