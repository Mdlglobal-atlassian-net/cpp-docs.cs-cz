---
title: /NOPDB
description: Možnost/NOPDB zachovává DUMPBIN v načítání a hledání souborů PDB pro informace o symbolech.
ms.date: 12/04/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 7b0c01e59b52bcec6ddf09416dd6aac9999527a6
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856966"
---
# <a name="nopdb"></a>/NOPDB

Oznamuje DUMPBIN, že nenačítá a hledá soubory databáze programu (PDB) pro informace o symbolech.

## <a name="syntax"></a>Syntaxe

> **/NOPDB**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení se služba DUMPBIN pokusí načíst soubory PDB pro své cílové spustitelné soubory. DUMPBIN používá tyto informace k porovnávání adres s názvy symbolů. Tento proces může být časově náročný, pokud jsou soubory PDB velké nebo je nutné je načíst ze vzdáleného serveru. Možnost **/NOPDB** určuje, že DUMPBIN tento krok přeskočí. Vytiskne pouze adresy a informace o symbolech, které jsou k dispozici ve spustitelném souboru.

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Nastavení Možnosti linkeru/NOPDB v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **příkazového řádku** > **linkeru** .

1. V poli **Další možnosti** přidejte možnost **/NOPDB** . Změny uložte kliknutím na **OK** nebo **použít** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také:

\ [příkazového řádku DUMPBIN](dumpbin-command-line.md)
\ [možností DUMPBIN](dumpbin-options.md)
[Odkaz DUMPBIN](dumpbin-reference.md)
