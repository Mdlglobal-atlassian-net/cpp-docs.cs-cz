---
title: / ALIGN (zarovnání oddílů) | Dokumentace Microsoftu
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
ms.openlocfilehash: cb92d4b16be7903004831ffb25e2891f498a8989
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718247"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
