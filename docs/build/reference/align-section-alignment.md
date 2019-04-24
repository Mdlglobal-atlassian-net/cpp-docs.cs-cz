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
ms.openlocfilehash: d8d2e6a859c68af473d49dc04b76f0a15056aa56
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295263"
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

Je možné změnit zarovnání určitého oddílu s parametrem zarovnat [/SECTION](section-specify-section-attributes.md) možnost.

Hodnota zarovnání, který zadáte, nemůže být menší než největšímu zarovnání oddílu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Zvolte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
