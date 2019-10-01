---
title: /LINKREPROTARGET (název souboru reprodukci propojení)
description: Možnost linkeru nebo nástroje knihovny pro nastavení názvu cílového souboru pro propojení reprodukci.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: d629c4c2665239d03f38569677fa579b6c8d37e0
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712685"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET (název souboru reprodukci propojení)

Instruuje linker nebo nástroj knihovny, aby vygeneroval propojení reprodukci, jenom když má cíl zadaný název souboru.

## <a name="syntax"></a>Syntaxe

> **/LINKREPROTARGET:** _název souboru_

### <a name="arguments"></a>Arguments

**/LINKREPROTARGET:** _název souboru_@no__t – 2
Název cílového souboru, který se má filtrovat Odkaz reprodukci je generován pouze v případě, že pojmenovaný soubor je výstupní cíl. Názvy souborů, které obsahují mezery, musí být uzavřeny do dvojitých uvozovek. Název souboru by měl obsahovat základní název a příponu, ale ne cestu.

## <a name="remarks"></a>Poznámky

Možnost **/LINKREPROTARGET** slouží k zadání názvu cílového souboru pro vygenerování *propojení reprodukci* pro. Reprodukci propojení je sada artefaktů sestavení, které umožňují Microsoftu reprodukování problému, ke kterému dochází v době propojování nebo během operací knihovny. Nástroj Linker nebo knihovna vytvoří odkaz reprodukci při zadání možnosti [/LINKREPRO](linkrepro.md) nebo při nastavení proměnné prostředí `link_repro` v prostředí pro sestavení příkazového řádku.

Možnost **/LINKREPROTARGET** je užitečná v komplexních sestaveních, která vyvolávají nástroj Linker nebo knihovna více než jednou. Umožňuje zadat konkrétní cíl pro reprodukci propojení, jako je například *problém. dll*. Umožňuje vygenerovat reprodukci propojení pouze v případě, že nástroj vytváří konkrétní soubor.

Další informace o tom, jak a kdy vytvořit propojení reprodukci, najdete v části [věnovaném](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) předávat dál v tématu [postup nahlášení problému se sadou C++ nástrojů Microsoftu](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Pokud má mít možnost **/LINKREPROTARGET** nějaký účinek, musí být nastavené možnosti **/LINKREPRO** a [/out](out-output-file-name.md) .

**/LINKREPROTARGET** je k dispozici počínaje verzí Visual Studio 2019 verze 16,1.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > **linker** >  stránka vlastností**příkazového řádku** .

1. Do pole **Další možnosti** zadejte možnost **/LINKREPROTARGET:** _název souboru_ . Kliknutím na **tlačítko OK** aplikujte změnu.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční příručka linkeru MSVC](linking.md)\
[MSVC Možnosti linkeru](linker-options.md)\
[/LINKREPRO](linkrepro.md)
