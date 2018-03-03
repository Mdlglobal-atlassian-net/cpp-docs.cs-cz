---
title: "/ FILEALIGN (Align oddíly v souborech) | Microsoft Docs"
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 753f6c5fade4211654246aec19af60c60706d7ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="filealign-align-sections-in-files"></a>/ FILEALIGN (Align oddíly v souborech)

**/Filealign** – možnost linkeru slouží k určení zarovnání oddílů zapsána do výstupního souboru jako násobkem zadanou velikost.

## <a name="syntax"></a>Syntaxe

> __/ FILEALIGN:__*velikost*

### <a name="parameters"></a>Parametry

*velikost*  
Část zarovnání velikost v bajtech, které musí být násobek dvou.

## <a name="remarks"></a>Poznámky

**/Filealign** linkeru Chcete-li zarovnat každý oddíl ve výstupním souboru na hranici, která je násobkem způsobí, že *velikost* hodnotu. Ve výchozím nastavení linkeru nepoužívá zarovnání pevnou velikost.

**/Filealign** možnost lze použít k efektivní využití disku, nebo aby stránka načte z disku rychlejší. Menší velikost oddílu může být užitečné pro aplikace, které běží na menší zařízení, nebo chcete zachovat menší soubory ke stažení. Zarovnání oddílů na disku neovlivňuje zarovnání v paměti.

Použití [DUMPBIN](dumpbin-reference.md) zobrazíte informace o oddílech ve výstupním souboru.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránka vlastností v **Linkeru** složky.

1. Zadejte název možnosti **/filealign:** a velikost v **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)