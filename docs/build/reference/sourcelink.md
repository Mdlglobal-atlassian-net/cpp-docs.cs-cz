---
title: / SOURCELINK (Sourcelink zahrnout soubor PDB)
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: a5a01ca56a49791a608c5c836312c7728e9328c3
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978280"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/ SOURCELINK (zahrnout odkaz na zdroj souboru PDB)

Určuje konfigurační soubor zdrojového odkazu pro zahrnutí souboru PDB vygenerován linkerem.

## <a name="syntax"></a>Syntaxe

> **/ SOURCELINK:**_název souboru_

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Určuje konfiguraci ve formátu JSON soubor, který obsahuje jednoduché mapování místní cesty souborů na adresy URL ve kterém se dá načíst zdrojový soubor pro zobrazení ladicím programem. Další informace o formátu tohoto souboru najdete v tématu [schématu JSON odkaz zdroje](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Poznámky

Odkaz na zdroj je jazyk a zdrojového nezávislá systém pro poskytování ladění zdrojového kód pro binární soubory. Zdrojový odkaz se podporuje pro nativní binární soubory C++ v sadě Visual Studio 2017 verze 15.8 spuštění. Přehled odkazu na zdroj, naleznete v tématu [odkazu na zdroj](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Informace o tom, jak používat odkaz na zdroj ve vašich projektech a jak vygenerovat soubor SourceLink jako součást projektu, naleznete v tématu [pomocí zdrojového odkazu](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Nastavení parametru linkeru/sourcelink v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/sourcelink:**_filename_ a klikněte na tlačítko **OK** nebo **použít**uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
