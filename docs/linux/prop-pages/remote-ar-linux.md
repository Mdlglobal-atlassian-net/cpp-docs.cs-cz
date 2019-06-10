---
title: Archiv vzdálených vlastnosti (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 00de4ac56a9ce390672019c7fe5a838367823100
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821265"
---
# <a name="remote-archive-properties-c-linux"></a>Archiv vzdálených vlastnosti (C++ Linux)

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Vlastnost | Popis
--- | ---
Vytvoří index archivu | Vytvoří index archivu (jako provádí taky ranlib). Tato možnost může urychlit propojování a omezit závislost v rámci vlastní knihovny.
Vytvořit tenký archiv | Vytvořte tenký archiv.  Tenký archiv obsahuje relativní cesty k objektům namísto vložení objekty.  Přepnutí mezi tenkým a normálním vyžaduje odstranění existující knihovnu.
Bez upozornění při vytvoření | Nezobrazí upozornění, pokud nebo když se knihovna vytváří.
Oříznout časové razítko | Použít pro časová razítka a identifikátory UID/gids.
Potlačit úvodní nápis | Nezobrazovat číslo verze.
Podrobnosti | Podrobnosti
Další možnosti | Další možnosti.
Výstupní soubor | Parametr/out přepisuje výchozí název a umístění programu, který nástroj lib vytváří.
Archivačního programu | Určuje program, který se má volat během propojování statických objektů, nebo cestu k Archivačnímu programu ve vzdáleném systému.
Časový limit archivačního programu | Časový limit vzdáleného archivačního programu, v milisekundách.
Kopírovat výstup | Určuje, jestli se má kopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače.

::: moniker-end
