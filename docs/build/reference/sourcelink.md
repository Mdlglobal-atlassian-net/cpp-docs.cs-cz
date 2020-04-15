---
title: /SOURCELINK (zahrnutí souboru Sourcelink do souboru PDB)
description: Referenční příručka k možnosti propojovacího programu /SOURCELINK v jazyce Microsoft C++.
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336072"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (Zahrnout zdrojový odkaz do PDB)

Určuje konfigurační soubor zdrojového propojení, který má být zahrnut do souboru PDB generovaného propojovacím programem.

## <a name="syntax"></a>Syntaxe

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>Argumenty

*Název_souboru*<br/>
Určuje konfigurační soubor ve formátu JSON, který obsahuje jednoduché mapování cest místních souborů na adresy URL pro zdrojové soubory, které se mají zobrazit v ladicím programu. Další informace o formátu tohoto souboru naleznete v tématu [Source Link JSON Schema](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Poznámky

Zdrojový odkaz je jazyk- a zdroj řízení agnostik systém pro poskytování ladění zdroje pro binární soubory. Zdrojový odkaz je podporován pro nativní binární soubory C++ začínající ve Visual Studiu 2017 verze 15.8. Přehled zdrojového odkazu naleznete v tématu [Zdrojový odkaz](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md). Informace o použití zdrojového odkazu v projektech a o tom, jak vygenerovat soubor SourceLink jako součást projektu, naleznete [v tématu Použití zdrojového odkazu](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Nastavení možnosti propojovacího zařízení /SOURCELINK v sadě Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** pro projekt. Další informace naleznete [v tématu Nastavení kompilátoru c++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazového řádku** **propojovacího** > programu **Vlastnosti** > konfigurace.

1. V poli **Další možnosti** **`/SOURCELINK:`** _`filename`_ přidejte a pak zvolte **OK** nebo **Použít,** chcete-li změny uložit.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](linker-options.md)
