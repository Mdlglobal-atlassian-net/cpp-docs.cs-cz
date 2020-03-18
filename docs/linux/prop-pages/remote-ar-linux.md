---
title: Vlastnosti vzdáleného archivu (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: dc20eecef9947581ca87b9489285bc058a249e26
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446810"
---
# <a name="remote-archive-properties-c-linux"></a>Vlastnosti vzdáleného archivu (C++ Linux)

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

::: moniker range=">=vs-2017"

| Vlastnost | Popis |
|--|--|
| Vytvořit index archivu | Vytvořte index archivu (jako v ranlib). Tato možnost umožňuje zrychlit propojení a snížit závislosti v rámci vlastní knihovny. |
| Vytvořit tenký archiv | Vytvořte tenký archiv.  Tenký archiv obsahuje relativní cesty k objektům místo vložení objektů.  Přepínání mezi tenkými a normálními nároky vyžaduje odstranění existující knihovny. |
| Bez upozornění při vytvoření | Neupozorňuje na to, jestli je knihovna vytvořená. |
| Zkrátit časové razítko | Pro časová razítka a UID/Gids použijte nulu. |
| Potlačit úvodní nápis | Nezobrazovat číslo verze |
| Podrobnosti | Podrobnosti |
| Další možnosti | Další možnosti: |
| Výstupní soubor | Možnost/OUT přepisuje výchozí název a umístění programu, který vytvoří lib. |
| Archivačního programu | Určuje program, který se má volat během propojování statických objektů, nebo cestu k archivačnímu programu ve vzdáleném systému. |
| Časový limit archivačního programu | Časový limit vzdáleného archivačního programu v milisekundách |
| Kopírovat výstup | Určuje, zda se má kopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače. |

::: moniker-end
