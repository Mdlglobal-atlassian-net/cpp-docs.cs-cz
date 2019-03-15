---
title: / FILEALIGN (zarovnání oddílů v souborech)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814472"
---
# <a name="filealign-align-sections-in-files"></a>/ FILEALIGN (zarovnání oddílů v souborech)

**/Filealign** – možnost linkeru umožňuje určit zarovnání oddílů zapsána do výstupního souboru jako násobek čísla zadané velikosti.

## <a name="syntax"></a>Syntaxe

> __/ FILEALIGN:__*velikost*

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Velikost zarovnání oddílu v bajtech, které musí být mocninou čísla 2.

## <a name="remarks"></a>Poznámky

**/Filealign** – možnost linkeru, aby zarovnat jednotlivé oddíly výstupního souboru na hranici, která je násobkem způsobí, že *velikost* hodnotu. Ve výchozím nastavení propojovací program nepoužívá zarovnání pevnou velikost.

**/Filealign** možnost lze zefektivnit využití disku, nebo aby stránka načte z disku rychleji. Menší velikost oddílu může být užitečné pro aplikace spuštěné na menších zařízeních, nebo zachovat menší soubory ke stažení. Zarovnání oddílů na disku neovlivní zarovnání v paměti.

Použití [DUMPBIN](dumpbin-reference.md) zobrazíte informace o oddílech výstupního souboru.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránku vlastností v **Linkeru** složky.

1. Zadejte název možnosti **/filealign:** a velikost v **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
