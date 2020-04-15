---
title: Vlastnosti vzdáleného archivu (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364293"
---
# <a name="remote-archive-properties-c-linux"></a>Vlastnosti vzdáleného archivu (C++ Linux)

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

::: moniker range=">=vs-2017"

| Vlastnost | Popis |
|--|--|
| Vytvoření archivního indexu | Vytvořte archivní index (jak to dělá ranlib). Tato možnost může urychlit propojení a snížit závislost v rámci své vlastní knihovny. |
| Vytvořit tenkou archivaci | Vytvořte tenký archiv.  Tenká archivace obsahuje relativní cesty k objektům namísto vkládání objektů.  Přepnutí mezi tenkým a normálním vyžaduje odstranění existující knihovny. |
| Žádné upozornění na vytvoření | Neupozorní, zda nebo kdy je knihovna vytvořena. |
| Zkrátit časové razítko | Pro časová razítka a uidy/gids použijte nulu. |
| Potlačit spouštěcí banner | Nezobrazovat číslo verze. |
| Verbose | Verbose |
| Další možnosti | Další možnosti. |
| Výstupní soubor | Možnost /OUT přepíše výchozí název a umístění programu, který vytvoří lib. |
| Archiver | Určuje program, který má být vyvolán během propojování statických objektů, nebo cestu k archivátoru ve vzdáleném systému. |
| Časový čas archivátoru | Časový rozsah vzdáleného archivátoru v milisekundách. |
| Kopírovat výstup | Určuje, zda se má zkopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače. |

::: moniker-end
