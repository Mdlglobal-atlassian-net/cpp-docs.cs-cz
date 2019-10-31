---
title: /NOPDB
description: Možnost/NOPDB zachovává DUMPBIN v načítání a hledání souborů PDB pro informace o symbolech.
ms.date: 10/29/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 3b745049517888d13de245d4e29be3985c122ada
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145733"
---
# <a name="nopdb"></a>/NOPDB

Oznamuje DUMPBIN, že nenačítá a hledá soubory databáze programu (PDB) pro informace o symbolech.

## <a name="syntax"></a>Syntaxe

> **/NOPDB**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení se služba DUMPBIN pokusí načíst soubory PDB pro své cílové objekty, knihovny nebo spustitelné soubory. DUMPBIN používá tyto informace k porovnávání adres s názvy symbolů. Tento proces může být časově náročný, pokud jsou soubory PDB velké nebo je nutné je načíst ze vzdáleného serveru. Možnost **/NOPDB** určuje, že DUMPBIN tento krok přeskočí. Vytiskne pouze adresy a informace o symbolech, které jsou k dispozici v souboru objektu, knihovně nebo spustitelném souboru.

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
