---
title: Makra proměnné prostředí
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: 7f7f8a05545658142001b75ac78975251185a033
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272608"
---
# <a name="environment-variable-macros"></a>Makra proměnné prostředí

NMAKE dědí definice maker pro proměnné prostředí, které existují před zahájením relace. Pokud proměnná byla nastavena v prostředí operačního systému, je k dispozici jako makra NMAKE. Zděděné názvy jsou převedeny na velká písmena. Vyvolá se před předzpracování dědičnosti. Pomocí možnosti /E způsobit maker zděděno z proměnné prostředí pro přepsání jakékoli makro se stejným názvem v souboru pravidel.

Makra proměnné prostředí lze redefinovat v relaci, a tím změní příslušné proměnné prostředí. Můžete také změnit proměnných prostředí pomocí příkazu SET. Chcete-li změnit proměnné prostředí v relaci pomocí příkazu SET nezmění odpovídající – makro, ale.

Příklad:

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

V tomto příkladu mění `PATH` změní příslušné proměnné prostředí `PATH`; přidá `\nonesuch` do cesty.

Pokud proměnná prostředí je definovaný jako řetězec, který by byla syntaxe chybná v souboru pravidel, žádné – makro se vytvoří a je generována bez upozornění. Pokud hodnota proměnné obsahuje znak dolaru ($), NMAKE interpretovat jako začátek volání makra. Použití makra může způsobit neočekávané chování.

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](special-nmake-macros.md)
