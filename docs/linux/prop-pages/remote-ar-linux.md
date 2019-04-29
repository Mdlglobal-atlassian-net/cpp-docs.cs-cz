---
title: Archiv vzdálených vlastnosti (C++ Linux)
ms.date: 9/26/2017
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: bcd0e0eef16addc60743000b6ed8cba12276e29c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392996"
---
# <a name="remote-archive-properties-c-linux"></a>Archiv vzdálených vlastnosti (C++ Linux)

Vlastnost | Popis
--- | ---
Vytvoří index archivu | Vytvoří index archivu (viz taky ranlib).  Může urychlit propojování a omezit závislost v rámci vlastní knihovny.
Vytvořit tenký archiv | Vytvořte tenký archiv.  Tenký archiv obsahuje relativepaths na objekty namísto vložení objekty.  Přepnutí mezi tenkým a normálním vyžaduje odstranění existující knihovnu.
Bez upozornění při vytvoření | Neupozorňovat, pokud při se knihovna vytváří.
Oříznout časové razítko | Použít pro časová razítka a identifikátory UID/gids.
Potlačit úvodní nápis | Nezobrazí číslo verze.
Podrobnosti | Podrobnosti
Další možnosti | Další možnosti.
Výstupní soubor | Parametr/out přepisuje výchozí název a umístění programu, který nástroj lib vytváří.
Archivačního programu | Určuje program, který se má volat během propojování statických objektů, nebo cestu k Archivačnímu programu ve vzdáleném systému.
Časový limit archivačního programu | Časový limit vzdáleného archivačního programu, v milisekundách.
Kopírovat výstup | Určuje, jestli se má kopírovat výstupní soubor sestavení ze vzdáleného systému do místního počítače.
