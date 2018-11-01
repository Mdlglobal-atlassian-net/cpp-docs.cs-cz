---
title: /ALIGN (zarovnání oddílů)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: b68ec42db9c927fe8f56dad8f5670059359a1843
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665787"
---
# <a name="align-section-alignment"></a>/ALIGN (zarovnání oddílů)

## <a name="syntax"></a>Syntaxe

> **/ ALIGN**[**:**_číslo_]

### <a name="arguments"></a>Arguments

*Číslo*<br/>
Hodnota zarovnání v bajtech.

## <a name="remarks"></a>Poznámky

**/ALIGN** Určuje zarovnání jednotlivých oddílů uvnitř lineárního adresního prostoru programu. *Číslo* argument je vyjádřen v bajtech a musí být mocninou čísla 2. Výchozí hodnota je 4 kB (4096). Linker vydá upozornění, pokud zarovnání vytvoří image v neplatný.

Pokud vytváříte aplikaci, jako jsou ovladače zařízení, neměli byste potřebovat změnit zarovnání.

Je možné změnit zarovnání určitého oddílu s parametrem zarovnat [/SECTION](../../build/reference/section-specify-section-attributes.md) možnost.

Hodnota zarovnání, který zadáte, nemůže být menší než největšímu zarovnání oddílu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Zvolte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
